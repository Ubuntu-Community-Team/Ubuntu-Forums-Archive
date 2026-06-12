---
title: "Can't even start Ubuntu"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by ChuckPerkins on 2009-09-04
I am lost!
I burned a CD and loaded ubuntu 9.04 and when Windows (XP Home) starts, it gives me the option of starting Ubuntu.  Then it goes into some DOS-looking thing and I can't get past it.
 
Now what do I do?
 
Also, Can I use it without Windows?  I mean as its own OS?
 
Any help here would be greatly appreciated.

---

### Post by Ms_Angel_D on 2009-09-04
Which version did you download?
what exactly does the screen say that you get?

If it's the live cd version then it sounds like a possible bad burn, I would try burning a disk again at a very low speed.

To answer the 2nd question. Ubuntu is an operating system, I use it only and nothing else no windows. Just as windows is an Operating system, so is Ubuntu. If your asking this question then perhaps you should read a bit more before attempting an install. Here's some recommended reading [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by ChuckPerkins on 2009-09-04
Thanks!!!  I will try another burn and then try to load it on a slave HD.  Will that work if I put the slave into its own computer?

---

### Post by Ms_Angel_D on 2009-09-04
I personally have never tried it, you should either google "Ubuntu two hard drives" or wait until someone who knows comes along.

;)

---

### Post by mike555 on 2009-09-04
sounds like your trying to run Ubuntu inside Windows ...... you should put in the cd , then restart your computer ...... it should start on the cd and then you can try Ubuntu without installing anything ...... it will run quite slow because it is running off the cd , but it will let you try it before installing......

---

### Post by LewRockwell on 2009-09-04
> **ChuckPerkins said:**
> I am lost!
I burned a CD and loaded ubuntu 9.04 and when Windows (XP Home) starts, it gives me the option of starting Ubuntu.  Then it goes into some DOS-looking thing and I can't get past it.
 
Now what do I do?
 
Also, Can I use it without Windows?  I mean as its own OS?
 
Any help here would be greatly appreciated.

Angel is correct about the possibility of a bad burn session for your current CD

However, if you have access to several other computers you might want to try the disk in others before you go to the trouble of slow-burning another one

We have come across machines that would not run the LiveCD properly without any additional tweaking and futzing(in most cases we don't mess with those motherboards as we have as many as we want to drag to the shop)

.

---

### Post by dragonlyre on 2009-09-04
And about running it off the slave, yes. If you used wubi, there is a drop down box where it asks where you want to install it. Choose the name of the slave driver and then install as usual.

---

### Post by Shapps on 2009-09-15
> **mike555 said:**
> sounds like your trying to run Ubuntu inside Windows ...... you should put in the cd , then restart your computer ...... it should start on the cd and then you can try Ubuntu without installing anything ...... it will run quite slow because it is running off the cd , but it will let you try it before installing......

I did the same thing without success. Then uninstalled it and tried to run off the CD.....no luck!  Any ideas?

---

### Post by nothingspecial on 2009-09-15
In what way have you had no luck?

Did you set your bios to boot from cd?

---

### Post by halitech on 2009-09-15
when it gets to the DOS looking place, what exactly does it say?

Also, what video card do you have?

As far as installing it on your slave drive, certainly you can. When it gets to where its asking where to install, do a manual partitioning and select the /dev/sdb partition (Linux doesn't use C:\ or D:\ to denote drives)

---

### Post by Shapps on 2009-09-15
> **Shapps said:**
> I did the same thing without success. Then uninstalled it and tried to run off the CD.....no luck!  Any ideas?

Originally:

1. tried to install Ubuntu within Windows as a try out.  But could not get it to boot up using the change option in the DOS section where it asks you which OS system you want to use.  It did come up with the Ubuntu logo but then reverted back to DOS

2. Read the information given to other questioner about booting from the disk.  So uninstalled Ubuntu.   But the DOS section still shows it available.

3. Put the disk in the hole again, turned off computer and then restarted.  Again it stopped at the Dos message.  Then told me that some file or another was missing if I tried Ubuntu (but actually booted up in Windows when I switched options).

So, there you have it....or not, in my case!

Tony

---

### Post by LewRockwell on 2009-09-15
> **Shapps said:**
> I did the same thing without success. Then uninstalled it and tried to run off the CD.....no luck!  Any ideas?

New trouble-calls should have their own new thread

Otherwise issues and subsequent advice and recommendations become absolutely confusing and in some cases result in the necessity of starting from scratch with your whole system

nobody wants that...

.

---

### Post by LewRockwell on 2009-09-15
> **Shapps said:**
> Originally:

1. tried to install Ubuntu within Windows as a try out.  But could not get it to boot up using the change option in the DOS section where it asks you which OS system you want to use.  It did come up with the Ubuntu logo but then reverted back to DOS

2. Read the information given to other questioner about booting from the disk.  So uninstalled Ubuntu.   But the DOS section still shows it available.

3. Put the disk in the hole again, turned off computer and then restarted.  Again it stopped at the Dos message.  Then told me that some file or another was missing if I tried Ubuntu (but actually booted up in Windows when I switched options).

So, there you have it....or not, in my case!

Tony

help us help you

(start a new thread and then proceed...cut and paste to new thread as desired)

give us your specific information and details

which version?

was the md5checksum correct?

did you burn your CD-R optical media at the slowest burn speed possible?

did you use the proper program and process to burn the iso correctly?

even if you do everything correctly...have you tried the LiveCD in other machines?

even if it works successfully in other machines...it may not work with EVERY machine out there...

if you have tried all of these and need further ideas...you should try the alternate install version(note that it does not have the livecd test-drive function...only the install function)

.

---

### Post by Rufus T. Firefly on 2009-09-15
I wonder if you're making the same mistake that I did.

I found this useful:

[http://ubuntuforums.org/showthread.php?t=111589&highlight=nero](http://ubuntuforums.org/showthread.php?t=111589&highlight=nero)

---

### Post by 3rdalbum on 2009-09-15
I believe the "DOS section" that Shapps is referring to is the Windows bootloader (remember, they used Wubi to install Ubuntu). They have now removed Ubuntu but the Windows bootloader still has an entry for it.

You must boot up from the CD. Change your BIOS settings so that it tries to boot from CD *before* looking at the hard disks.

To ChuckPerkins: What is displayed on the screen at the point where you can't get any further?

---

### Post by Shapps on 2009-09-18
> **nothingspecial said:**
> In what way have you had no luck?

Did you set your bios to boot from cd?
Yes, I changed the Bios to boot from the CD  (which is the one that I was sent, not a CD produced from a download).

I removed/uninstalled all references to Ubuntu (with the exception of the word 'Ubuntu' coming up at the start...and which I have no idea of how to remove it) it is offered as an alternative to Widows; if you do nothing the computer then boots up in Widows as usual

I'm obviously going wrong somewhere  -  but where?

Tony
[email]tony@shapps.myzen.co.uk[/email]

---

### Post by nothingspecial on 2009-09-18
And will it not boot from the cd?

If so you have a bad cd...

or a bad cd drive

Try downloading and burning at the slowest possible speed.

You`re not giving much information here.

---

### Post by Shapps on 2009-09-18
Thanks to all of you for your help and assistance,  I now have Ubuntu up and running from the original CD.

The only thing is that the keyboard (A Microsoft one) is configured slightly differently and I cannot find the 'ambersand' for emails  i.e. the bit that goes between your name and the server.uk or ,com or whatever!

Tony (!)  shapps.myzen.co.uk

---

### Post by LewRockwell on 2009-09-18
> **Shapps said:**
> Thanks to all of you for your help and assistance,  I now have Ubuntu up and running from the original CD.

The only thing is that the keyboard (A Microsoft one) is configured slightly differently and I cannot find the 'ambersand' for emails  i.e. the bit that goes between your name and the server.uk or ,com or whatever!

Tony (!)  shapps.myzen.co.uk

Cheerios Mates!

what did you do to get it to work for you

Good Day Mates!

.

---

