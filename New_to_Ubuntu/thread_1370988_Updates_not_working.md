---
title: "Updates not working"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by SW90 on 2010-01-02
After discovering that ubuntu 9.10 did not work well with my computer, i went back to what i had previously, ubuntu 8.04. I know from past experience that when you install this, you need to download maaany updates, but when i try to update..

i click check (to check for updates) every time there will be about 29 things it tries to download - package information or something. It always stops at the 27th, and will give me this message

> 
W: A error occurred during the signature verification. The respository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid; BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
(repeat that 3 times or so)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release)
(repeat that 3 times or so)

W: Some index files failed to download, they have been ignored, or old ones used instead.


this prevents me from downloading programs as well.

---

### Post by xtjacob on 2010-01-02
To add the keys you can use this command: ```
gpg --keyserver keyserver.ubuntu.com --recv [last eight characters]; gpg --export --armor [last eight characters] | sudo apt-key add -
``` For example to add the keys you are missing you would put this in the terminal:```
gpg --keyserver keyserver.ubuntu.com --recv 437D05B5; gpg --export --armor 437D05B5 | sudo apt-key add -
```

---

### Post by SW90 on 2010-01-02
> **xtjacob said:**
> To add the keys you can use this command: ```
gpg --keyserver keyserver.ubuntu.com --recv [last eight characters]; gpg --export --armor [last eight characters] | sudo apt-key add -
``` For example to add the keys you are missing you would put this in the terminal:```
gpg --keyserver keyserver.ubuntu.com --recv 437D05B5; gpg --export --armor 437D05B5 | sudo apt-key add -
```

when you say [last eight characters] what are you refering to?

---

### Post by SW90 on 2010-01-02
oh srry, i see

---

### Post by xtjacob on 2010-01-02
The last eight characters of the key that it reports missing. For example it says it is missing the key with a signature of 40976EAF437D05B5, so you take the last 8 characters "437D05B5" and replace [last eight characters] with it.

---

### Post by SW90 on 2010-01-02
> **xtjacob said:**
> To add the keys you can use this command: ```
gpg --keyserver keyserver.ubuntu.com --recv [last eight characters]; gpg --export --armor [last eight characters] | sudo apt-key add -
``` For example to add the keys you are missing you would put this in the terminal:```
gpg --keyserver keyserver.ubuntu.com --recv 437D05B5; gpg --export --armor 437D05B5 | sudo apt-key add -
```

I put that in and got this back

> gpg: Invalid option "--recv437D05B5"
gpg: WARNING: nothing exported


---

### Post by xtjacob on 2010-01-02
You need to put a space after "-recv".

---

### Post by SW90 on 2010-01-02
did that, and got this

> gpg: requesting key 437D05B5 from hkp server keyserve.ubuntu.com
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'keyserve.ubuntu.com'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


---

### Post by xtjacob on 2010-01-02
You put keyserve.ubuntu.com not keyserver.ubuntu.com

---

### Post by SW90 on 2010-01-02
> gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
OK

and i still can't get past the 27th package

---

### Post by xtjacob on 2010-01-02
You could try selecting a different mirror and see if that works, System-> Administration-> Software Sources->Download From and choose the server you want. If you want to you can click on choose best server.

---

### Post by SW90 on 2010-01-02
Thanks, it is now downloading all 415 updates!

---

