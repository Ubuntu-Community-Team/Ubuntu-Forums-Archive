---
title: "Install Sun JRE via Command Line"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by pukestain on 2010-12-26
I need to install the SUN JRE via command line and can't find the commands to get apt to use the correct repositories can someone point me in the right direction? I need to:

* update apt-get repositories via command line to use sun's universe
* install the sun jre via apt-get.

I cannot use the Software Center as this is a server installation with only a command-line interface. 

Many thanks.
-j

---

### Post by cottfcfan on 2010-12-26
sudo apt-get install sun-java6-plugin sun-java6-jre

That should work.

---

### Post by sgosnell on 2010-12-26
Sun doesn't have a universe repository, AFAIK.  Open terminal and run the following commands

Add partner repository using the following command

    ```
sudo add-apt-repository &#8220;deb http://archive.canonical.com/ lucid partner&#8221;
```

Update the source list

    ```
sudo apt-get update
```

Now install sun java packages using the following commands

    ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

The above command will download all the required packages and begins the installation, you&#8217;ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue.

You&#8217;ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing.

---

### Post by sammiev on 2010-12-26
If you agree with the DLJ license terms. Select Yes and if Yes doesn't highlight, just use the Tab key to highlight and press enter. :)

---

### Post by pukestain on 2010-12-27
Sgosnel,

this looks exactly like what I need, however the first command is failing for me:

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”

sudo: add-apt-repository: command not found.

```

Any ideas? I am running 10.04

---

### Post by sgosnell on 2010-12-27
I got that from a couple of sites via Google.  If that won't work, add the part in double quotes to your /etc/apt/sources.list file and then do the rest.  I'm running Debian, so I can't check that part.

---

### Post by oldos2er on 2010-12-27
> **pukestain said:**
> Sgosnel,

this looks exactly like what I need, however the first command is failing for me:

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”

sudo: add-apt-repository: command not found.

```

Any ideas? I am running 10.04

Should be **apt-add-repository**.

---

### Post by pukestain on 2010-12-27
Thanks all for the help. I wound up having to install python-software-properties to get apt-add-repository to work.

---

