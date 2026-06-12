---
title: "Installing Ubuntu on Crashed Windows?.."
date: 2010-12-05
forum: New to Ubuntu
---

### Post by duckonastick on 2010-12-05
Alright, sorry I'm a total noob with Ubuntu.  My Windows laptop crashed in this weird way where every time I try to log in, it crashes again, and I can't open cmd prompt to do system restore, and I basically can't do anything at all because it's stuck in a loop of crashing and restarting and then crashing again as soon as it gets to the login screen.  

So I thought I'd install Ubuntu, save all my files, and maybe just stick with using Ubuntu.

Is this possible given the crashing situation?  Will I lose all my files if I try to install Ubuntu over Windows while it's doing its crashing thing?

Thanks.

---

### Post by sikander3786 on 2010-12-05
Welcome to Ubuntu and the forums :-)

I would first suggest to boot an Ubuntu Live CD/USB (you've got that?).

That way you would be able to test all your hardware with Ubuntu and secondly, you can mount your Windows partitions, extract data from those partitions to a safe location and then install Ubuntu.

We need to know more about your partition setup to advise more efficiently. Go to Applications > Accessories > Terminal and post the output of this command.

```
sudo fdisk -lu
```

Feel free to ask anything you need ;-)

---

### Post by MooPi on 2010-12-05
You don't want to install Ubuntu right away. Just use the Live CD option to save your file to an alternate location, external/DVD/flash drive ?. Then you can install without loosing data. Good luck :)

---

### Post by dargaud on 2010-12-05
If you have an available partition, it's certainly possible. If not it may be hard as you'd need to resize the partition and it's usually best done from within Windows.
My advice is to GET ANOTHER DISK (40$), put it inside your laptop, install Ubuntu on it, get a USB adapter for your old disk (15$) and copy your data over, keeping your old disk as backup. It's safer, faster and no-hassle.

---

### Post by mlentink on 2010-12-05
I recommend to first try and rescue your files. 
Do you have access to antoher computer? If so, download the Ubunbt LiveCD iso and burn it to a disk. Boot up your own computer with the LiveCD (you may have to change the boor order in your BIOS), and wait until you have the ubuntu desktop on you screen. Now mount the harddisk (most likely already mounted) navigate to your Documents folder and move them someplace safe (USB-harddisk perhaps?).
After this, check that everything works as it should with ubuntu. If you're satisfied you can choose the 'Install Ubuntu' option. If not, at least your files are safe, and you can try to salvage your Windows with some rescue disk or reinstall with the original.

---

### Post by duckonastick on 2010-12-05
So you're saying go here?  [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

And USB is exactly the same, right?  Cause I'm out of blank CDs.

And I definitely won't lose my files by doing this?

---

### Post by mlentink on 2010-12-05
That's the right location for sure. Use the USB option (use 'Show me how' if you don know how to do it)

As long as you do not actually install Ubuntu, it will leave your harddisk untouched.

---

### Post by duckonastick on 2010-12-05
Okay thanks, I got up to that point and when I put the USB and restarted, I chose run from USB..it went to cmd prompt and listed all the things it was doing to load, but right now it's stuck on

[           0.597241    [<c010363e>] kernel_thread_helper+0x6/0x10

it's been there for like ten minutes, is it supposed to take this long to run?

---

### Post by sikander3786 on 2010-12-05
Check MD5SUM of downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, use unetbootin this time.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by duckonastick on 2010-12-05
I used UNetbootin, but the same thing happened.  

[http://i52.tinypic.com/24nhhcw.jpg](http://i52.tinypic.com/24nhhcw.jpg)

It stops there and doesn't load Ubuntu.  I left it for like 20 minutes.

---

### Post by Jerry N on 2010-12-05
> **duckonastick said:**
> 
Is this possible given the crashing situation?  Will I lose all my files if I try to install Ubuntu over Windows while it's doing its crashing thing?

You **WILL** lose all your files if you try to install Ubuntu over Windows, crashing or not.  It is possible that you have a hardware problem rather than a corrupted Windows install.  In that case, you might not be able to do an Ubuntu install.  If a hard disk failure is the problem, you should still be able to run the live version of Ubuntu though.  Since creating a USB version of Ubuntu is an extra step, I would suggest getting some blank CDs and some proper image burning software such as ImgBurn or Ashanti (Nero is great if you have it available) to create a bootable CD.  Don't try to use Windows CD burning software to create an image from the downloaded ISO file.  Don't try to install anything at all on your hard drive until you have extracted the files you want to save.  Of course you have backups of all those files, don't you?

Jerry

---

### Post by sikander3786 on 2010-12-05
> **duckonastick said:**
> I used UNetbootin, but the same thing happened.  

[http://i52.tinypic.com/24nhhcw.jpg](http://i52.tinypic.com/24nhhcw.jpg)

It stops there and doesn't load Ubuntu.  I left it for like 20 minutes.
Did you check the MD5SUM of downloaded image?

That sounds like a hardware issue to me now. Windows keeps crashing and Linux Kernel also panics, definitely not good.

First of all I would opt to do a memtest on your RAM.

You can do that from a Live USB as well.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

That test might run over-night so, be prepared!

---

### Post by wilee-nilee on 2010-12-05
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Really since this is a open source forum you will get the instructions to just overwrite the windows when this may not be needed, if you would like to have it still.

Post this script read out it will separate the wheat from the chaff so to speak and let us see whats going on.

---

### Post by duckonastick on 2010-12-05
I can't get Ubuntu Live to boot though, it just gets stuck midway..so I don't see how that bootscript thing will work.  I'm on a different computer right now cause the other one just won't do anything except load the login screen and then crash before I get logged in.

---

### Post by wilee-nilee on 2010-12-05
> **duckonastick said:**
> I can't get Ubuntu Live to boot though, it just gets stuck midway..so I don't see how that bootscript thing will work.  I'm on a different computer right now cause the other one just won't do anything except load the login screen and then crash before I get logged in.

Okay I tried, if you want to second guess support then so be it good luck.;)

---

### Post by duckonastick on 2010-12-05
I'm not second guessing you, sorry, I just meant since I can't even boot..how do I do bootscript?  Like put it on a flash drive and boot with the flash drive?

---

### Post by Jerry N on 2010-12-05
> **wilee-nilee said:**
> Okay I tried, if you want to second guess support then so be it good luck.;)

He said he couldn't get linux to boot at all - that doesn't sound like second guessing the expert to me!

You might try downloading Puppy Linux to see if that will boot.  It's simpler than Ubuntu and will boot much faster, if it boots.  You can use Puppy to copy your files from the HD to a USB drive and then proceed with the trouble shooting.

Jerry

---

### Post by wilee-nilee on 2010-12-05
> **Jerry N said:**
> He said he couldn't get linux to boot at all - that doesn't sound like second guessing the expert to me!

You might try downloading Puppy Linux to see if that will boot.  It's simpler than Ubuntu and will boot much faster, if it boots.  You can use Puppy to copy your files from the HD to a USB drive and then proceed with the trouble shooting.

Jerry

Alright Karnac thanks for hanging at funk and wagnells and reading their mind.;)

Let the person speak for themselves did you not listen to your mothers advice?

The bootscript is a long text file that gives the what is where of everything, it is more then relevant here.

---

### Post by duckonastick on 2010-12-05
> **Jerry N said:**
> He said he couldn't get linux to boot at all - that doesn't sound like second guessing the expert to me!

You might try downloading Puppy Linux to see if that will boot.  It's simpler than Ubuntu and will boot much faster, if it boots.

Jerry

Thanks, I'll try it..hope it boots.

---

### Post by eriktheblu on 2010-12-05
Hard to run the boot script (or anything for that matter) when the OS doesn't initialize.

Do the MD5sum check. If that clears, try hitting Enter the next time it hangs. Sometimes that works.

Oh, and always second guess the experts ;)

---

