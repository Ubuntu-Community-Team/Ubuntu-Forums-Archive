---
title: "Make Error [make: *** [hydra-sip.o] Error 1]"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by System Monitor on 2009-01-06
While installing hydra I get this error after using the make command, make: *** [hydra-sip.o] Error 1
```
sam@sam-laptop:~/Desktop/hydra-5.4-src$ make
make: Warning: File `pw-inspector.c' has modification time 2.3e+08 s in the future
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c  
gcc -I. -Wall -O2 -c hydra-pcnfs.c  
gcc -I. -Wall -O2 -c hydra-rexec.c  
gcc -I. -Wall -O2 -c hydra-nntp.c  
gcc -I. -Wall -O2 -c hydra-socks5.c  
gcc -I. -Wall -O2 -c hydra-telnet.c  
hydra-telnet.c: In function ‘service_telnet’:
hydra-telnet.c:177: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
hydra-telnet.c:191: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
hydra-telnet.c:198: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc -I. -Wall -O2 -c hydra-cisco.c  
gcc -I. -Wall -O2 -c hydra-http.c  
gcc -I. -Wall -O2 -c hydra-ftp.c  
gcc -I. -Wall -O2 -c hydra-imap.c  
gcc -I. -Wall -O2 -c hydra-pop3.c  
gcc -I. -Wall -O2 -c hydra-smb.c  
gcc -I. -Wall -O2 -c hydra-icq.c  
gcc -I. -Wall -O2 -c hydra-cisco-enable.c  
gcc -I. -Wall -O2 -c hydra-ldap.c  
gcc -I. -Wall -O2 -c hydra-mysql.c  
gcc -I. -Wall -O2 -c hydra-http-proxy.c  
gcc -I. -Wall -O2 -c hydra-smbnt.c  
gcc -I. -Wall -O2 -c hydra-mssql.c  
gcc -I. -Wall -O2 -c hydra-snmp.c  
gcc -I. -Wall -O2 -c hydra-cvs.c  
gcc -I. -Wall -O2 -c hydra-smtpauth.c  
gcc -I. -Wall -O2 -c hydra-sapr3.c  
gcc -I. -Wall -O2 -c hydra-ssh2.c  
gcc -I. -Wall -O2 -c hydra-teamspeak.c  
gcc -I. -Wall -O2 -c hydra-postgres.c  
gcc -I. -Wall -O2 -c hydra-rsh.c  
gcc -I. -Wall -O2 -c hydra-rlogin.c  
gcc -I. -Wall -O2 -c hydra-oracle-listener.c  
hydra-oracle-listener.c:10:2: warning: #warning "The Oracle Listener module does not work yet"
gcc -I. -Wall -O2 -c hydra-svn.c  
gcc -I. -Wall -O2 -c hydra-pcanywhere.c  
gcc -I. -Wall -O2 -c hydra-sip.c  
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1

```

---

### Post by LowSky on 2009-01-06
From whay I'm looking at the program is looking for  a file destination that was never created and File `pw-inspector.c' has modification time 2.3e+08 s in the future, which means something was set wrong with this file compared to the system time keeping

---

### Post by System Monitor on 2009-01-06
Sorry I had forgot that I reset the time for a completely different reason.
Here is the code with the time at todays date.
```
sam@sam-laptop:~/Desktop/hydra-5.4-src$ make
gcc -I. -Wall -O2 -o pw-inspector pw-inspector.c
gcc -I. -Wall -O2 -c hydra-vnc.c  
gcc -I. -Wall -O2 -c hydra-pcnfs.c  
gcc -I. -Wall -O2 -c hydra-rexec.c  
gcc -I. -Wall -O2 -c hydra-nntp.c  
gcc -I. -Wall -O2 -c hydra-socks5.c  
gcc -I. -Wall -O2 -c hydra-telnet.c  
hydra-telnet.c: In function ‘service_telnet’:
hydra-telnet.c:177: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
hydra-telnet.c:191: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
hydra-telnet.c:198: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
gcc -I. -Wall -O2 -c hydra-cisco.c  
gcc -I. -Wall -O2 -c hydra-http.c  
gcc -I. -Wall -O2 -c hydra-ftp.c  
gcc -I. -Wall -O2 -c hydra-imap.c  
gcc -I. -Wall -O2 -c hydra-pop3.c  
gcc -I. -Wall -O2 -c hydra-smb.c  
gcc -I. -Wall -O2 -c hydra-icq.c  
gcc -I. -Wall -O2 -c hydra-cisco-enable.c  
gcc -I. -Wall -O2 -c hydra-ldap.c  
gcc -I. -Wall -O2 -c hydra-mysql.c  
gcc -I. -Wall -O2 -c hydra-http-proxy.c  
gcc -I. -Wall -O2 -c hydra-smbnt.c  
gcc -I. -Wall -O2 -c hydra-mssql.c  
gcc -I. -Wall -O2 -c hydra-snmp.c  
gcc -I. -Wall -O2 -c hydra-cvs.c  
gcc -I. -Wall -O2 -c hydra-smtpauth.c  
gcc -I. -Wall -O2 -c hydra-sapr3.c  
gcc -I. -Wall -O2 -c hydra-ssh2.c  
gcc -I. -Wall -O2 -c hydra-teamspeak.c  
gcc -I. -Wall -O2 -c hydra-postgres.c  
gcc -I. -Wall -O2 -c hydra-rsh.c  
gcc -I. -Wall -O2 -c hydra-rlogin.c  
gcc -I. -Wall -O2 -c hydra-oracle-listener.c  
hydra-oracle-listener.c:10:2: warning: #warning "The Oracle Listener module does not work yet"
gcc -I. -Wall -O2 -c hydra-svn.c  
gcc -I. -Wall -O2 -c hydra-pcanywhere.c  
gcc -I. -Wall -O2 -c hydra-sip.c  
hydra-sip.c:4:25: error: openssl/ssl.h: No such file or directory
hydra-sip.c:5:25: error: openssl/err.h: No such file or directory
hydra-sip.c:6:25: error: openssl/md5.h: No such file or directory
hydra-sip.c: In function ‘md5_crypt’:
hydra-sip.c:24: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:24: error: (Each undeclared identifier is reported only once
hydra-sip.c:24: error: for each function it appears in.)
hydra-sip.c:26: error: ‘MD5_CTX’ undeclared (first use in this function)
hydra-sip.c:26: error: expected ‘;’ before ‘c’
hydra-sip.c:31: warning: implicit declaration of function ‘MD5_Init’
hydra-sip.c:31: error: ‘c’ undeclared (first use in this function)
hydra-sip.c:32: warning: implicit declaration of function ‘MD5_Update’
hydra-sip.c:33: warning: implicit declaration of function ‘MD5_Final’
hydra-sip.c:24: warning: unused variable ‘md5_raw’
hydra-sip.c: In function ‘sip_register’:
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1


```

---

