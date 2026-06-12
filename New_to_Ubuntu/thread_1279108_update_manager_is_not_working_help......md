---
title: "update manager is not working help....."
date: 2009-09-30
forum: New to Ubuntu
---

### Post by blake7 on 2009-09-30
it says this when i try to down load its packages

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

what does thiss mean and can i solve it 

thank you and have a good one

---

### Post by drs305 on 2009-09-30
You need to import the public key. I just ran the command and didn't get the BADSIG error message. 

Use the last 8 alphanumeric characters in the error message and import them into this command:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys **[COLOR="DarkRed"]437D05B5 0C5A2783[/COLOR]** && gpg --export --armor **[COLOR="DarkRed"]437D05B5 0C5A2783[/COLOR]** | sudo apt-key add - 

```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by blake7 on 2009-10-03
that did not work it still have has the same problem can any one elae help and how did this happen in the frist place???

---

### Post by drs305 on 2009-10-03
This will import the Medibuntu repository and key:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

If it doesn't work, remove your existing link to Medibuntu in your sources.list and run the command again.

For the other repository, remove the authentication key for [email]ftpmaster@ubuntu.com[/email] and Reload. It will probably say you need the public key. Take the alphanumberic code in the error message and insert it twice  in this command:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys **[COLOR="DarkRed"]insert.here[/COLOR]** && gpg --export --armor **[COLOR="DarkRed"]insert.here[/COLOR]** | sudo apt-key add -

```
.

---

