---
title: "Help a noob get his drivers set up?"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by noobius on 2011-06-04
Hi!  I'm an ubuntu noob.  I just got sick of windows during the last blue screen and decided to try it out.  So far I like it.  The only problem is I'm not very familiar with it.

I'm trying to install a driver but i'm not sure who to trust.  I found this...
[http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/](http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/)
Is that legit?

The driver I want to install is for a ATI HD 4830 PCI E 512M to play starcraft....

If i can get starcraft 2 to work on ubuntu I can troll my windows using friends :)

Right now it's just a pixelated mess when I try and play it.

(i have the driver downloaded just don't know how to install)

\\:D/

---

### Post by howefield on 2011-06-04
Try using Additional Drivers to see if there are drivers available from the Ubuntu repositories.

System > Administration > Additional Drivers

---

### Post by Laforge129 on 2011-06-04
> **noobius said:**
> Hi!  I'm an ubuntu noob.  I just got sick of windows during the last blue screen and decided to try it out.  So far I like it.  The only problem is I'm not very familiar with it.

I'm trying to install a driver but i'm not sure who to trust.  I found this...
[http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/](http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/)
Is that legit?

The driver I want to install is for a ATI HD 4830 PCI E 512M to play starcraft....

If i can get starcraft 2 to work on ubuntu I can troll my windows using friends :)

Right now it's just a pixelated mess when I try and play it.

(i have the driver downloaded just don't know how to install)

\\:D/

If you can't figure out Ubuntu, [You can try other distros and play with Linux a little more]("http://www.paulstechtalk.com/the-pen-is-mightier-than-the-megabyte/").   You should also try Playonlinux!

```
Sudo apt-get install playonlinux
```

and don't forget to install wine

```
Sudo apt-get install wine
```

---

### Post by noobius on 2011-06-04
System > Administration >  ?

"Additional Drivers" is not an option on my system when i go there :(

I have "hardware drivers" as an option but there is no flexibility to change anything other than remove the one I have (ATI/AMD proprietary FGLRX graphics driver)

---

### Post by noobius on 2011-06-04
> **Laforge129 said:**
> If you can't figure out Ubuntu, [You can try other distros and play with Linux a little more]("http://www.paulstechtalk.com/the-pen-is-mightier-than-the-megabyte/").   You should also try Playonlinux!

```
Sudo apt-get install playonlinux
```and don't forget to install wine

```
Sudo apt-get install wine
```

I just started...   I can figure it out ... (i get by with a little help from my friends)...thanks for the tip, i'll check it out after I have the right driver set up.

---

### Post by Laforge129 on 2011-06-04
> **noobius said:**
> I just started...   I can figure it out ... (i get by with a little help from my friends)...thanks for the tip, i'll check it out after I have the right driver set up.

Are you sure you don't already have the drivers installed??

---

### Post by noobius on 2011-06-04
Sorry, I'm not sure of anything cause i'm kinda green to all this
but it says I have 
"ATI/AMD proprietary FGLRX graphics driver"
When i go to system > admin..> hardware drivers

and I downloaded one from AMD for the ATI HD 4830 just now for linux and want to install that one from my download directory "ati-driver-installer-11-5-x86.x86_64.run"

Am I making any sense/  sorry i'm so lost LOL!:P

BTW thank you for helping me out!

---

### Post by Laforge129 on 2011-06-04
> **noobius said:**
> Sorry, I'm not sure of anything cause i'm kinda green to all this
but it says I have 
"ATI/AMD proprietary FGLRX graphics driver"
When i go to system > admin..> hardware drivers

and I downloaded one from AMD for the ATI HD 4830 just now for linux and want to install that one from my download directory "ati-driver-installer-11-5-x86.x86_64.run"

Am I making any sense/  sorry i'm so lost LOL!:P

BTW thank you for helping me out!

I know what you doing wrong.  change the properties on the file and make it executable.   Use the file manager and edit the properties then go to the permissions tab and tick the make executable.   

Once that is done hit OK.  Go into your terminal and go to the directory where this file is then do this:
```
sudo ./ati-driver-installer-11-5-x86.x86_64.run
```

---

### Post by noobius on 2011-06-05
I may or may not have my drivers installed but now whn I go to install starcraft all I get is the starcraft 2 end user license thing with no other options ... no Ok button on the bottom... welp maybe ubuntu is not my thing...

---

### Post by jtarin on 2011-06-05
> **noobius said:**
> I may or may not have my drivers installed but now whn I go to install starcraft all I get is the starcraft 2 end user license thing with no other options ... no Ok button on the bottom... welp maybe ubuntu is not my thing...Your Starcraft installation files....are they on CD?DVD? Do your Starcraft installation files end in the file extension ".exe."?

---

### Post by noobius on 2011-06-05
> **jtarin said:**
> Your Starcraft installation files....are they on CD?DVD? Do your Starcraft installation files end in the file extension ".exe."?



Yeah it's an executable.... I got starcraft to install before but this time the end user thingy  doesn't let me get past it for some reason I can not explain.

---

### Post by jtarin on 2011-06-05
Starcraft is a Windows application it will not run under Linux. You might be able to run it using WINE.

---

### Post by noobius on 2011-06-05
> **jtarin said:**
> Starcraft is a Windows application it will not run under Linux. You might be able to run it using WINE.

Yeah, I'm using wine.... i had it installed before but I was going to reinstall it after I got my drivers installed (was giving me an error, thought that may fix it)....starcraft has hella problems and the support is almost as good as AT&T (sarcasim)

---

