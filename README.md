# ca
Certificate Authority for The Fat Hacker Root CA

### References
- [Jamie Nguyen's - OpenSSL Certificate Authority - v1.0.4](https://jamielinux.com/docs/openssl-certificate-authority/)

## Root CA Setup
Setup Directories
```
cd /root/ca
mkdir certs crl newcerts private
chmod 700 private
touch index.txt
echo 1000 > serial
```
Create Key
```
openssl genrsa -aes256 -out private/ca.key.pem 4096
chmod 400 private/ca.key.pem
```
Create Certificate
```
openssl req -config openssl.cnf \
      -key private/ca.key.pem \
      -new -x509 -days 7300 -sha256 -extensions v3_ca \
      -out certs/ca.cert.pem
chmod 444 certs/ca.cert.pem
```
