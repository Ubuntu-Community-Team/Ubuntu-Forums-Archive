---
title: "Using encrypted 'SafeStick' pendrives"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by cwwtech on 2010-11-10
Folks!
I work for a medium size company here in Welsh Wales & we are considering moving, at least, some of our current Windows machines over to the newest Ubuntu! We are also pretty much virgins when it comes to Linux! 
Before we can even think about moving to Linux - we need to be able to use our large current stock of encrypted pendrives [SafeStick] on Ubuntu.
We have been in touch with the makers of the pen drives - & apparently there is a beta version of the S/W available for Linux [which they have sent to us] - its command line based, which we would like to put in a script BUT we can't get it to work without giving Root permissions, to the DEV folder, to all & sundry! 
It seems that opening up this folder would screw up security [though i'm happy to be proved wrong on this]? 
Anyone out there with any ideas pleeeaaase?
 
cheers
John

---

### Post by toekneewood on 2010-11-10
Have you got any examples of the commands or a script?

---

### Post by cwwtech on 2010-11-10
We were originally told to use the following script:
sudo ./safestick

---

### Post by HermanAB on 2010-11-10
Howdy,

I would not trust the encryption on Safestick.  I'm not saying it is bad, but I won't trust it.

See this:
[http://www.aeronetworks.ca/howtos/luks-usb-howto.html](http://www.aeronetworks.ca/howtos/luks-usb-howto.html)
[http://www.aeronetworks.ca/howtos/LUKS-Mount-FreeOTFE.pdf](http://www.aeronetworks.ca/howtos/LUKS-Mount-FreeOTFE.pdf)

---

### Post by cwwtech on 2010-11-10
Herman,
Thanks for the reply. Unfortunately we have already bought a stack of these SafeSticks at £40+ ea - so I can't see my boss rushing to get rid.
I will pass this on to him of course as I do like stirring the pot occassionally:).
cheers
John

---

### Post by toekneewood on 2010-11-10
Is it possible to post the contents of the "./safestick"  or is it a monster script

---

### Post by toekneewood on 2010-11-10
Truecrypt is another option.  [http://www.truecrypt.org/]("http://www.truecrypt.org/")

It supports Windows, mac & Linux.  I think it also has a portable client

---

### Post by cwwtech on 2010-11-10
Sorry if I sound like a dunderhead but that was pretty much the script they sent us. it worked but had to be run as SUDO [if thats the right way to say it]..
cheers
John

---

### Post by Skavenger0 on 2010-11-10
Im looking at the same problem funnily enough and have also started a thread. 
From the sounds of it I'm trying to use the same firmware update. However I think the file you are referring to ```
./safestick
``` is not a script but a compiled single file application.

My problem is I want to change the system permissions to decrypt the volume and mount the drive as a standard user without the use of sudo. Which is what SafeStick and the SafeStick readme implies.

[http://ubuntuforums.org/showthread.php?t=1618117]("http://ubuntuforums.org/showthread.php?t=1618117")

---

### Post by softek on 2010-11-11
Hi,  UK Distributor Softek have provided further information in this thread:  [http://ubuntuforums.org/showthread.php?t=1618117](http://ubuntuforums.org/showthread.php?t=1618117)

---

### Post by toekneewood on 2010-11-11
> **cwwtech said:**
> Sorry if I sound like a dunderhead but that was pretty much the script they sent us. it worked but had to be run as SUDO [if thats the right way to say it]..
cheers
John
Using "sudo" is defiantly the correct way to do anything admin.  When you do a clean Ubuntu install the "root" password is encrypted.  You should never set a password against that.  You then put yourself in the admin/suduer group and user the word "sudo" and front of any admin tasks.  Example
Add SuperUser Privileges
```

sudo usermod -a -G admin tony
sudo apt-get install apache2

```

---

### Post by toekneewood on 2010-11-11
RU OK with the above link (post #10)or do you need more info?

On the permissions side 777 would equate to
```

User = read, write, execute
Group = read, write, execute
Other = read, write, execute
and 764 would equate to
User = read, write, execute
Group = read, write, none
Other = read, none, none

```
so 777 is full control, so try to back off the permissions and use a group, rather than the group "other"

---

