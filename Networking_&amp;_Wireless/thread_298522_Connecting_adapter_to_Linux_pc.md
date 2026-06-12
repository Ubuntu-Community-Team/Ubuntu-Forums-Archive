---
title: "Connecting adapter to Linux pc"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Kulluminatii on 2006-11-12
I need help in getting DSL to work on my Ubuntu pc. I have DSL on my XP system, and have recently bought a router and a adapter. I successfully installed the router onto the Windows XP system, but the adapter( which I am trying to install onto my Ubuntu pc) I am having problems with. Im used to following the easy user interface to setup these things....but I cant do that now

I bought these two things.

LINKSYS Wireless-G Broadband Router with SRX200
Model NO: WRT54GX2
[http://www.newegg.com/Product/Produc...82E16833124050](http://www.newegg.com/Product/Produc...82E16833124050)

LINKSYS Compact Wireless-G USB Adapter
Model NO: WUSB54GC
[http://www.newegg.com/Product/Produc...82E16833124187](http://www.newegg.com/Product/Produc...82E16833124187)

I already have the adapter hooked up to the Ubuntu pc...so thats out of the way.

I am trying to follow this guide

[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)

But I cant figure out half of the stuff he is doing, I am still pretty new to this whole linux thing.

*UPDATE*
Well i got to step 2 in this guide.

[http://www.ubuntuforums.org/showthread.php?t=192588](http://www.ubuntuforums.org/showthread.php?t=192588)

I downloaded ndiswrapper 1.8 on my xp pc, burned it to a cd and followed the directions. I opened up the terminal and typed

'tar zxvf ndiswrapper-version.tar.gz'

This is what happened

'tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors'

Now what do I do?

---

### Post by FrodoB on 2006-11-12
You are not getting the correct full file name. The version is supposed to be the actual number.

Open a terminal and type 

$ tar xvzf ndiswrapper

at this point click on the "tab" key and the terminal shell will complete the name for you, and then press enter.

---

### Post by Kulluminatii on 2006-11-12
Oooh..hehe...

---

### Post by Kulluminatii on 2006-11-13
When I pressed 'tab', the pc just made a beeping sound, it did not do anything. I typed it in again, pressed 'tab' then enter, and it gave me the same error as before.

---

### Post by FrodoB on 2006-11-13
That is just telling you the the file is not in the directory that you are in.  Just give an ls command to see the available filenames in the current directory.

If you download the file to your desktop, the default, once you open a terminal just:

$ cd Desktop

$ ls

should show the file.

Move it to your home

$ mv ndiswrapper* ~

$ cd

now do and ls

$ ls


and it should be in your home.

Well you get the idea.

If you want to go back to your home just give a cd alone:

$ cd

---

### Post by Kulluminatii on 2006-11-14
ok...lets see how that goes.

---

### Post by Kulluminatii on 2006-11-14
> **FrodoB said:**
> 

$ cd Desktop

$ ls

should show the file.

**Move it to your home**

$ mv ndiswrapper* ~

$ cd

now do and ls

$ ls


and it should be in your home.

Well you get the idea.

If you want to go back to your home just give a cd alone:

$ cd

When you said move it to your home, did the code below move it or did you mean move it by myself. Because I just thought it moved it and it gave me the same error once I was done with it, but I feel like im on the right track:p

---

### Post by Kulluminatii on 2006-11-15
Anyone?

---

### Post by FrodoB on 2006-11-16
You have to be in the directory that you put the file into. Whichever one that is.

---

### Post by Kulluminatii on 2006-11-17
you mean ndiswrapper..well...its on the desktop, any recommendation where I should put it?

---

### Post by FrodoB on 2006-11-17
In you home directory. Go to the middle Places location on the top menu and select Home Folder and put it in there.  That will be where you are when you open a terminal window.  Just type "ls" and you will see it there.

---

### Post by Kulluminatii on 2006-11-17
Ok, i'll try that asap

---

### Post by FrodoB on 2006-11-17
Wait! Have you just plugged it in and then opened a Terminal window and typed:

$ iwconfig

This device might be supported, some of them are Ralink chips. Show us the output of iwconfig.

---

### Post by Kulluminatii on 2006-11-19
crap...I need to do all this stuff I've been told..I will do this when I get back on to that other computer. Thank you for all your help

---

### Post by 3rdalbum on 2006-11-19
Download these files from the pages:

[http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
[http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)

Put them onto your Ubuntu computer and double-click the first one (ndiswrapper-utils). Click the "Install" button. You'll be asked for your password.

When it has been installed, double-click the second one (ndisgtk) and follow the same procedure.

Now you will find a new entry in your System > Administration menu, which is Ndiswrapper's GUI.

If the Debian packages don't work, you can try the manual installation according to the instructions you linked to.

[I]As discussed on IM:

1. The file is extracted to your desktop, so go into a terminal and type "cd Desktop".

2. Type "ls" to show a list of files and folders on your desktop. One of the folders will be probably say "ndiswrapper" or something like that.

3. Assuming the folder name is "ndiswrapper-0.1", you would type "cd ndiswrapper-0.1" to move the terminal into it.

4. I've never used Ndiswrapper, but I'm assuming that you've downloaded a source package of it. Therefore you will need to get the development libraries from your Ubuntu disc. This is simple: just do a "sudo apt-get install build-essential", inserting your disc when prompted.

5. Now give the rest of the file's instructions a whirl and if you have any problems, please post again or IM me.[/I]

---

### Post by Kulluminatii on 2006-11-25
I know its been forever but I finally got time to try it out.

I typed in 'iwconfig' and this is what popped up.

lo                                   no wireless extensions

sit0                                 no wireless extensions

---

### Post by Kulluminatii on 2006-11-25
[http://packages.ubuntu.com/dapper/mi...swrapper-utils](http://packages.ubuntu.com/dapper/mi...swrapper-utils)
[http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)

What do I download on both pages? There are so many diff types of it, im not 100% sure which ones to download.

---

### Post by FrodoB on 2006-11-25
Please provide the output of the:

lsusb

command when the device is plugged in.

---

### Post by Kulluminatii on 2006-11-26
The device is plugged in but I did not see lsusb or any output.:confused:

---

### Post by FrodoB on 2006-11-26
Serious issue, if it is not seen by lsusb, it is never going to work.  

Have you tried other USB ports on the system or just unplugging and replugging the device after a few seconds?

---

### Post by Kulluminatii on 2006-11-26
Their are two USB ports on my pc....I guess I should try the other one then:-k

---

