---
title: "Need help to install Xlite"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by criz84 on 2008-12-17
Hi there i just installed ubuntu for the first time n m trying to install xlite but it just wont install can any one plz help, if some one can post screen shots it would b gr8. thanks in advance

---

### Post by NewJack on 2008-12-22
Here is a link to a document created by a Ubuntu Forums User, [nickpaton]("http://ubuntuforums.org/member.php?u=25347")

Helped me with XLite, worked like a charm.

[http://nickpaton.fireflyinternet.co.uk/downloads/jjxlite.doc](http://nickpaton.fireflyinternet.co.uk/downloads/jjxlite.doc)

Make sure to thank him via PM for his work

---

### Post by namdung on 2008-12-22
> **criz84 said:**
> Hi there i just installed ubuntu for the first time n m trying to install xlite but it just wont install can any one plz help, if some one can post screen shots it would b gr8. thanks in advance

INSTALLATION:

In the terminal go to the directory where the downloaded file is eg. Desktop
> cd Desktop

Untar the file:
> tar -zxvf X-Lite_Install.tar.gz

This should expand the files into xten-xlite directory.
> cd xten-xlite

The executable is xtensoftphone, it should already have +x permission. If it does not, change the permission:
> chmod +x xtensoftphone

To run the executable:
> ./xtensoftphone

Copy the executable or a symbolic link file to a defined $PATH if you so wish.

---

### Post by mehdymahmood on 2009-11-04
root@mehdy-desktop:/usr/src/xten-xlite# ./xtensoftphone 
./xtensoftphone: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
how to get rid of this problem . please help me out

---

### Post by williammanda on 2009-11-05
I'm also having this problem and I have posted it on Counterpath.

[http://forums.counterpath.com/viewtopic.php?f=6&t=15795]("http://forums.counterpath.com/viewtopic.php?f=6&t=15795")

---

### Post by williammanda on 2009-11-10
It looks as though counterpath doesn't support libstdc++6 for x-lite but they did say that there will be a new x-lite for linux soon.
Here is the post:

[http://forums.counterpath.com/viewtopic.php?f=6&t=15815]("http://forums.counterpath.com/viewtopic.php?f=6&t=15815")

---

### Post by Gustavo86 on 2010-01-13
If you try to run X-lite in Ubuntu 9.10 and have the following error:

./xtensoftphone: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Just install the missing libraries. Download the package manually from:

[http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

Exactly from here:

[http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb)

It worked for me.

---

### Post by teddy0409 on 2010-02-19
[COLOR=DarkRed]sudo wget [http://counterpath.s3.amazonaws.com/downloads/X-Lite_Install.tar.gz](http://counterpath.s3.amazonaws.com/downloads/X-Lite_Install.tar.gz)

tar -zxvf X-Lite_Install.tar.gz

cd xten-xlite/

 chmod +x xtensoftphone

./xtensoftphone[/COLOR]


In the X-Lite 2.0 -->*System Settings-->Sip Proxy*

Enabled :                                  Yes
Display Name:                            Any Name
Username :                               [Your Voip Username]
Authorisation User:                   [Your Voip Username]           
Password:                                  [Your Voip Password]
Domain/Realm:                         sip.[VOIPCOMPANY].com
                                              (Please Refer to your Voip Provider)
SIP Proxy:                                 sip.[VOIPCOMPANY].com 
                                              Please Refer to your Voip Provider)
Outbound Proxy:                       nothing
Use Outbound Proxy:                 Default
Register:                                  Default
Voicemail SIP URL:                   nothing
Forword SIP URL:                     nothing

:popcorn:
Enjoy using X-Lite...

Simple

---

### Post by CShaum on 2010-05-02
I tried what was said here but I can't get it to install. It runs as long as the terminal window is open But when i close it. It also closes X-lite. How do I install it Thanks.

---

### Post by damo12 on 2010-05-03
[FONT="Comic Sans MS"]I'm having the same problem with Ubuntu 10.04 64 bit.  Would be extremely grateful if anyone has any suggestions.[/FONT]

---

### Post by oldos2er on 2010-05-03
When you close a terminal with running processes, those processes are killed too. You can cause a process to run in the background with "&" added to its name, e.g. "./xtensoftphone &" but you will still need to keep the terminal open. Using & this way frees up the terminal prompt for other uses.

If xtensoftphone doesn't require any input or output monitoring, run it with Alt-F2.

---

### Post by scenarist on 2010-05-15
Try this>>>

**How-To Fix libstdc++5 Dependency Problem in Ubuntu 9.10**



[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/)

---

### Post by eminentsedition on 2010-06-22
> **damo12 said:**
> [FONT="Comic Sans MS"]I'm having the same problem with Ubuntu 10.04 64 bit.  Would be extremely grateful if anyone has any suggestions.[/FONT]

I got this to work using the following website.
[http://www.hackourlives.com/ubuntu-10-04-lucid-lynx-libstdc-so-5/](http://www.hackourlives.com/ubuntu-10-04-lucid-lynx-libstdc-so-5/)

---

### Post by SuperDupes on 2010-09-08
[http://ftp.us.debian.org/debian/pool....6-18_i386.deb]("http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb")

worked for me.

Man, the linux version is way uglier than the windows version....

I guess that's the price you pay for open source sometimes...

---

