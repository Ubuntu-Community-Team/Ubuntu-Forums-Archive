---
title: "Unable to install chrome on ubuntu 11.04"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by anohs on 2011-05-07
I just installed ubuntu 11.04 and when trying to install google chrome on it, I am been told by Ubuntu software center that "Wrong architecture 'i386'" 

I downloaded 32 bit setup from google...

---

### Post by J a c k on 2011-05-07
That's occurring because you're running the 64-bit architecture version of Ubuntu. Download the 64-bit version of Chrome.

---

### Post by AngusH on 2011-05-07
Alternatively, why not install the version from the repositories? Open up the software-center, search for "chromium", click on the bit labelled "chromium web browser" then hit install.
Installing the 64 bit google version should work just as well, but using the software center and the repositories makes things a little bit more automatic and easier to deal with.
Hope that helps
Angus

---

### Post by anohs on 2011-05-07
Sorry, But I am bit new to linux/ubuntu. What do we mean by "64-bit architecture version of Ubuntu" ? If I am not wrong, I am using 32 bit version of windows 7 on the same machine.

Is there too much difference between chrome and chromium??

---

### Post by AngusH on 2011-05-07
Apart from the colour scheme there isn't much that you'll notice. I believe chromium doesn't send of reports to google while chrome does but I could be wrong.
Angus

---

### Post by rx007 on 2011-05-07
> **anohs said:**
> Sorry, But I am bit new to linux/ubuntu. What do we mean by "64-bit architecture version of Ubuntu" ? If I am not wrong, I am using 32 bit version of windows 7 on the same machine.

Is there too much difference between chrome and chromium??

Just go to Ubuntu Software Center, and search for Chromium browser. I believe it is identical with Chrome. It will automatically choose your architecture (32bit or 64bit). :)

---

### Post by The Cog on 2011-05-07
> **anohs said:**
> Sorry, But I am bit new to linux/ubuntu. What do we mean by "64-bit architecture version of Ubuntu" ? If I am not wrong, I am using 32 bit version of windows 7 on the same machine.
What version of windows you have installed is not relevant because windows isn't running when you run Ubuntu. My guess is that you installed the 64-bit version of Ubuntu. If you run the command **uname -a** it will print some version information that should indicate whether you are running 32 or 64 bit.

---

### Post by anohs on 2011-05-07
thanks a lot for your replies.

I used wubi to install ubuntu on a separate partition on my disk. During the installation it didn't asked whether it is installing 32 bit or 64 bit ubuntu.

i tried with both the chrome installer, 32 bit and 64 bit. Both are showing same error "wrong architecture"

---

### Post by J a c k on 2011-05-07
Run the following commands in a terminal and paste their output here. ```
uname -a
```  ```
grep flags /proc/cpuinfo 
```

---

### Post by Rex Bouwense on 2011-05-07
Why don't you try to install Chromium web browser from the Ubuntu software center as has been suggested.  I believe that Chrome is merely a rebranded version of Chromium.  That way you should not have the problems that you are having (or at least you shouldn't.)

---

### Post by spikoley on 2011-05-07
> **Rex Bouwense said:**
> Why don't you try to install Chromium web browser from the Ubuntu software center as has been suggested.  I believe that Chrome is merely a rebranded version of Chromium.  That way you should not have the problems that you are having (or at least you shouldn't.)

+1  Besides the name I cannot tell the difference between the two.

---

### Post by anohs on 2011-05-07
> **The Cog said:**
> What version of windows you have installed is not relevant because windows isn't running when you run Ubuntu. My guess is that you installed the 64-bit version of Ubuntu. If you run the command **uname -a** it will print some version information that should indicate whether you are running 32 or 64 bit.
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jtarin on 2011-05-07
> **anohs said:**
> Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
As mentioned previously......you have installed the 64 bit architecture of Ubuntu. This will limit you to software available for this architecture.

---

### Post by anohs on 2011-05-08
> **jtarin said:**
> As mentioned previously......you have installed the 64 bit architecture of Ubuntu. This will limit you to software available for this architecture.

Is there any way to install 32 bit architecture of ubuntu using Wubi? As told before, i installed ubuntu using wubi and it didn't asked which (32/64 bit) to install??

Moreover, Why isn't the chrome package for 64 bit  working?

---

### Post by anohs on 2011-05-08
Can anyone tell me where can i find a beginner introduction to Ubuntu (stuff like how to install using terminal,how to access /etc......)???

I just installed ubuntu and don't wan't to use windows again, so please help.

---

### Post by Rex Bouwense on 2011-05-08
Read the third sticky at the beginning of the Beginner's Forum.  That will get you started in the right direction.  Also see:
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)
[http://www.omgubuntu.co.uk/natty/](http://www.omgubuntu.co.uk/natty/)
They may be what you are looking for.  Also a WUBI install of Ubuntu is not a true dual boot.  Ubuntu is merely installed as a program inside of Microsoft Windows.  It will react slower and a perhaps a little goofy.  It is not intended (I believe) as a long-term solution but only as a means to see if you like it or not.  If you want to keep Ubuntu you need to install along side of Microsoft Windows or install it as your only OS.

---

### Post by anohs on 2011-05-09
> **Rex Bouwense said:**
> Read the third sticky at the beginning of the Beginner's Forum.  That will get you started in the right direction.  Also see:
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)
[http://www.omgubuntu.co.uk/natty/](http://www.omgubuntu.co.uk/natty/)
They may be what you are looking for.  Also a WUBI install of Ubuntu is not a true dual boot.  Ubuntu is merely installed as a program inside of Microsoft Windows.  It will react slower and a perhaps a little goofy.  It is not intended (I believe) as a long-term solution but only as a means to see if you like it or not.  If you want to keep Ubuntu you need to install along side of Microsoft Windows or install it as your only OS.

I have two partition on my hard disk (C and D). I have installed windows 7 on C and wants to install ubuntu on D. What are the possible options I have, which will allow me to install ubuntu on D? I would prefer installing using USB flash drive (CD/DVD is bit costly here!!).

I don't have sufficient knowledge of ubuntu, so it would be great if you could give me some URLs which explain each and every step of installation :)

---

### Post by diablo75 on 2011-05-09
> **anohs said:**
> I have two partition on my hard disk (C and D). I have installed windows 7 on C and wants to install ubuntu on D. What are the possible options I have, which will allow me to install ubuntu on D? I would prefer installing using USB flash drive (CD/DVD is bit costly here!!).

I don't have sufficient knowledge of ubuntu, so it would be great if you could give me some URLs which explain each and every step of installation :)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you have Ubuntu running already and you're wanting to reinstall it from a USB, you can create one using the current install.  You will need:

- A 32-bit version of Ubuntu Desktop Edition in ISO form (which you can download from Ubuntu.com)

- A USB stick that's 1 GB or larger

Insert your USB stick and then click on your main menu (upper left corner).  Search for "startup" and you'll see a shortcut for Startup Disk Creator appear.  You'll use this to make your USB stick into a bootable stick.  This involves formating the stick (erasing it) and then copying the necessary files from the ISO to the stick.

When it's finished the stick will be bootable, but being able to boot from it will depend on whether or not your BIOS supports booting from removable devices such as USB flash drives.  You will also probably have to change your BIOS's boot order so it will search the USB stick for a bootable partition first before any other device.

If all goes well, it will load the Ubuntu Live environment from the stick and allow you to install the OS to the computer.  Along the way it will also allow you to remove or resize (shrink) other partitions that are on the computer so you can create space for a new Linux partition if you have to.

---

### Post by eb3ha4el on 2011-05-09
> **Rex Bouwense said:**
> Why don't you try to install Chromium web browser from the Ubuntu software center as has been suggested.  I believe that Chrome is merely a rebranded version of Chromium.  That way you should not have the problems that you are having (or at least you shouldn't.)


You mean that Chromium existed before Google Chrome came along?
interesting if it is true.

---

### Post by robgraves on 2011-05-09
> **eb3ha4el said:**
> You mean that Chromium existed before Google Chrome came along?
interesting if it is true.

true
[http://en.wikipedia.org/wiki/Chromium_%28web_browser%29](http://en.wikipedia.org/wiki/Chromium_%28web_browser%29)

---

### Post by ewaynec on 2011-06-04
This is so funny, ie weird. I do not want Chrome, I have never installed it, but every time I do a update it installs it. I delete it and the next update it installs it again. Right now there is no trace of it anywhere on my computer, but if I do a update it will get installed, I see it in the list of updates, I tell it not to install, and it installs it anyhow.
  One can't get it and one can't get rid of it.

---

### Post by jtarin on 2011-06-04
You've installed it at least once as it is not part of the regular Ubuntu install. To keep it from upgrading  use Synaptic. Use complete removal then highlight ,in Synaptic, the application you just removed and from the menu select Packages>Lock Version. There might be other ways to do this but this works.

---

### Post by lisati on 2011-06-07
Thread closed for review by staff.

---

