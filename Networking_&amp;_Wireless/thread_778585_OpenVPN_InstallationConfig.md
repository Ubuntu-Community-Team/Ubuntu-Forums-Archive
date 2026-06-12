---
title: "OpenVPN Installation/Config"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Aaron Tomsett on 2008-05-02
Hi,

I have a Hardy Heron Desktop installation of Ubuntu (updated from Gutsy).  I am trying to set up OpenVPN to test it before I install on a Server installation.

I've been following some of the many installation guides for OpenVPN online but have run into problems when running ./vars to set the system variables for easy-rsa.

I've copied the example config files from /usr/share/doc etc and edited the vars file as directed but when I execute it I get the following errors:

aaron@sirec-linux:/etc/openvpn/easy-rsa/2.0$ ./vars
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 10: HOME: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 11: RANDFILE: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 12: openssl_conf: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 17: oid_section: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 18: engines: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 37: default_ca: command not found
dir: cannot access =: No such file or directory
dir: cannot access \:\:KEY_DIR: No such file or directory
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 43: certs: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 44: crl_dir: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 45: database: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 46: new_certs_dir: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 48: certificate: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 49: serial: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 50: crl: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 51: private_key: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 52: RANDFILE: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 54: x509_extensions: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 60: default_days: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 61: 30: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 62: default_md: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 63: preserve: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 68: policy: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 72: countryName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 73: stateOrProvinceName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 74: organizationName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 75: organizationalUnitName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 76: commonName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 77: emailAddress: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 83: countryName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 84: stateOrProvinceName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 85: localityName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 86: organizationName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 87: organizationalUnitName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 88: commonName: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 89: emailAddress: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 93: default_bits: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 94: default_keyfile: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 95: distinguished_name: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 96: attributes: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 97: x509_extensions: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 111: string_mask: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 116: syntax error near unexpected token `('
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 116: `countryName                   = Country Name (2 letter code)'
NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/easy-rsa/2.0/keys

Is the openssl.cnf file being executed?  I've had a really good look at vars and openssl.cnf but I can't find anything out of place.  I've also tried googling for the errors I get but it seems no one else has asked the question before.

Can someone please help me?

Regards,

Aaron Tomsett.

---

### Post by The Cog on 2008-05-02
For some reason your vars script is trying to execute openssl.conf as a script. I guess your editing of vars went wrong, but unless you post the vars file (and a reference to the instructions you used as a guide), I don't see that we can help much.

Make sure there are no unwanted spaces around any equals signs in the vars script.

---

### Post by Aaron Tomsett on 2008-05-02
That's exactly what I though; I even copied the config file from the examples and re-edited but got exactly the same.

The tutorials I have still open in my browser are [http://www.thebakershome.net/?q=node/56](http://www.thebakershome.net/?q=node/56)
and
[http://openvpn.net/index.php/documentation/howto.html#install](http://openvpn.net/index.php/documentation/howto.html#install)

Here's my vars file, I've hidden some of my personal details from the bottom.

aaron@sirec-linux:/etc/openvpn/easy-rsa/2.0$ cat vars
# easy-rsa parameter settings

# NOTE: If you installed from an RPM,
# don't edit this file in place in
# /usr/share/openvpn/easy-rsa --
# instead, you should copy the whole
# easy-rsa directory to another location
# (such as /etc/openvpn) so that your
# edits will not be wiped out by a future
# OpenVPN package upgrade.

# This variable should point to
# the top level of the easy-rsa
# tree.
export EASY_RSA="`pwd`"

#
# This variable should point to
# the requested executables
#
export OPENSSL="openssl"
export PKCS11TOOL="pkcs11-tool"
export GREP="grep"

# This variable should point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=`$EASY_RSA/openssl.cnf $EASY_RSA`

# Edit this variable to point to
# your soon-to-be-created key
# directory.
#
# WARNING: clean-all will do
# a rm -rf on this directory
# so make sure you define
# it correctly!
export KEY_DIR="$EASY_RSA/keys"

# Issue rm -rf warning
echo NOTE: If you run ./clean-all, I will be doing a rm -rf on $KEY_DIR

# Increase this to 2048 if you
# are paranoid.  This will slow
# down TLS negotiation performance
# as well as the one-time DH parms
# generation process.
export KEY_SIZE=1024

# In how many days should the root CA key expire?
export CA_EXPIRE=3650

# In how many days should certificates expire?
export KEY_EXPIRE=3650

# These are the default values for fields
# which will be placed in the certificate.
# Don't leave any of these fields blank.
export KEY_COUNTRY="UK"
export KEY_PROVINCE="NA"
export KEY_CITY="London"
export KEY_ORG="xxxxxx"
export KEY_EMAIL="aaron.tomsett@xxxxx"

Thanks,

Aaron.

---

### Post by The Cog on 2008-05-02
I see a possible problem with this line:
```
export KEY_CONFIG=`$EASY_RSA/openssl.cnf $EASY_RSA`
```
in my examples directory, that line reads:
```
export KEY_CONFIG=`$EASY_RSA/whichopensslcnf $EASY_RSA`
```
I think that could be your problem.

---

### Post by txtiger on 2009-01-04
This was definitely the problem for me.  First -- the line in vars that reads 

export KEY_CONFIG=`$EASY_RSA/whichopensslcnf $EASY_RSA`

is not asking you to change it.  Leave it pointing to the whichopensslcnf file.

Second -- in my copy of vars from "...examples/2.0" there was a dot in the file name (i.e., whichopenssl.cnf).  The actual filename had no dot.  When I corrected the vars file to match the actual filename, all the errors went away and the ./vars, ./clean-all, ./build-ca went fine.   :P

---

