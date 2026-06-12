---
title: "[SOLVED] Best Remote Access Solution for Ubuntu Newbie (needs to be secure)"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by cr0ss0ver on 2007-08-17
I am pretty much a complete Linux newbie and have just installed Ubuntu 7.04 (Feisty Fawn) on a computer in my network.  This computer has to be located in a different area, so I need to remote into the computer to begin my learning and work.  I am very excited about learning more about Linux/Unix and am picking back up on a very basic working knowledge of Red Hat/Fedora that I haven't updated in like 2 yrs...so yeah, i guess i'm a total n00b

Anyways, I would really like to do a complete remote access session into this Ubuntu machine from my XP machine.  I have read about doing SSH, VNC tunneled through SSH, FreeNX, etc.  I am looking for some guidance on which of these is best and easiest for a newbie to understand.  In addition, I WOULD like for the session to be encrypted and am only going to be accessing the machine from inside of my LAN.

Thanks so much for this wonderful forum!

P.S.  This is a completely fresh install.  I have done nothing on the machine other than just install Ubuntu and logon once.  So, I know that maybe I need to update some source lists, etc and may need a little bit o help there

---

### Post by kevdog on 2007-08-17
Here's a guide for setting up FreeNx:  [http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219)

In both cases of FreeNx or Vnc tunneled through ssh, as a prerequisite you need to have an ssh server or ssh daemon up and running first.  I would probably start with getting ssh running.  You can even tunnel X sessions through ssh if you want (would work if client was a linux box or Windows box running cygwin).

Subtle difference however between vnc and freenx.  With VNC you would share the same session with the user on the other side (you both would be seeing the same screen, move the same mouse, etc).  With FreeNX you actually get a separate session and login.  Whatever you do is not seen by the other user and vice versa.

---

### Post by cr0ss0ver on 2007-08-17
kevdog,

Thanks so much!  That worked like a charm!!  The only thing that I missed was how to add the GPG key from the FreeNX download site, but i found that from another entry on this forum.  You did an excellent job drafting this very helpful tutorial!

---

### Post by kevdog on 2007-08-17
Can you give more specifics of what you had a problem with so I can update the tutorial??

---

### Post by cr0ss0ver on 2007-08-17
> **kevdog said:**
> Can you give more specifics of what you had a problem with so I can update the tutorial??

Sure, the area where I had to a little something extra on my machine was:

3.Download and install the seveas freenx packages

When I ran sudo aptitude update I received an error message saying No key could be found and I saw that it was for the line I had recently added into my sources list for FreeNX.  So, I am understanding that I have to have a key for the site to go forward with downloading and installing the package.  I found these instructions:

In order to install the appropriate gpg key, execute the following commands (as described on the Seveas home page):


Code:
gpg --keyserver subkeys.pgp.net --recv-keys 1135D466 
gpg --export --armor 1135D466 | sudo apt-key add -

From this thread on the forum:

[http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx]("http://ubuntuforums.org/showthread.php?t=97277&highlight=freenx")

That worked and allowed me to successfully run the steps required to update and then install.  I also received one warning not mentioned regarding "not being able to authenticate the RSA key".  It will allow you to continue though if you click Yes, so I'm not sure if that makes any difference or not, but wanted to let you know too.

It was awesome to have my new Ubuntu desktop up in front of me on my windoze machine.  Thanks so much again!!

---

### Post by kevdog on 2007-08-18
Thanks I added those steps to the tutorial.  I installed the freenx server such a long time ago, I dont even remember having done this.=D>

---

