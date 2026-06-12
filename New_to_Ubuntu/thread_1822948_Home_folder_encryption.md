---
title: "Home folder encryption"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by setspeed on 2011-08-11
When I installed 10.04 I was given the option to encryt my home folder.
I did this (and recorded the passphrase like a good boy). 
Does encryption incur a performance penalty? Is my computer constantly churning over, encrypting the records of every internet page I visit, and everything I do etc?
If so, how so I turn off home folder encryption?
 
Sorry if this is a stupid question!!

---

### Post by imortalninja161 on 2011-08-11
hay man ok first encryption does incur a slight penalty of resources but for a home client pc the resource usage should no be very noticeable. Put it this way the security features out way the slight extra usage

Secondly The only folder that is Reviving the benefits and resource usage of the encryption is the Home folder itself and all the contents inside of the folder.

NOTE: considering all files inside that file are encrypted if a file or folder is moved or copied out of the 'Home Folder" The content that has been move/copied is no longer encrypted.

So in short:

> Does encryption incur a performance penalty? :Yes but cosidering the ammount of data your pc will hold commpared to a mainframe or server very slight

> Is my computer constantly churning over, encrypting the records of every internet page I visit, and everything I do etcNope only encrypts what's is in the specified directory

I hope this helps

As for unencrypted follow these steps you need to press ctr-alt-F1 first and this will take you to the Terminal so make sure you have written down all the commands first

1. Backup the home directory while you are logged in
sudo cp -rp /home/user /home/user.backup

1.1. Check that your home backup has everything!!!

2. reboot into root via grub

3. Delete your home directory
rm -rf /home/user

4. Remove the packages
apt-get remove ecryptfs-utils libecryptfs0
5. Restore your home directory

mv /home/user.backup /home/user
6. reboot

7. Remove any of those .Private .ecryptfs folders
rm -rf ~/.Private
rm -rf ~/.ecryptfs

NOTE: The steps for unencrypted was originally posted by  [jemmrich]("http://ubuntuforums.org/member.php?u=272742")

Thanks 
Imortalninja161

---

### Post by scorp123 on 2011-08-11
> **setspeed said:**
>  Does encryption incur a performance penalty? Very very minimal at best. My 6 year old "Core Duo" (= 32 bit, one generation behind "Core 2 Duo" chips!) laptop works tip top with encryption turned on. I can work on it all day long without ever hearing the fan spin up. To hear the fans working I have to watch HD movies fullscreen. But then again this has nothing to do with encryption. Watching HD movies will get your fans spinning in any case, home folder encryption or not.

---

### Post by setspeed on 2011-08-11
OK, well I think I'll just leave it enabled then. I need to do something though, this computer runs like a 3 legged dog!!
It's an 8yr old (or thereabouts) HP Compaq nc4010, 1.6Ghz Pentium M(obile) chip, a gig of ram, 64mb ATI Radeon IGP 350M graphics. not running Unity. 
It's horrible - even typing this in Firefox the lag is about a second before what I type appears! Scrolling down a page is laggy and jerky. It's especially bad if I try and run a Youtube video in another tab at the same time...

Any suggestions as to what I can do to increase performance (other than install a lighter flavour of Linux)?

---

### Post by setspeed on 2011-08-11
Actually, I've just installed Chromium, and it seems to be quite a bit more responsive than Firefox. I'm just used to my FF extensions though...

Also, one other question - when I installed Ubuntu, this computer had 512mb ram in it. Since then I've managed to find another 512mb to put in it, so it's now got a gig. Do I need to increase my swap? It's only 478mb, and when I tried to hibernate last night it wouldn't do it and told me I didn't have enough swap space. How would I go about doing it?

One final question, for some reason when I suspend the computer, it never wakes up again properly, screen just stays black, keys and touchpad don't do anything, and I have to reboot. Is there anything I can do about this?

---

### Post by anlag on 2011-09-29
> **setspeed said:**
> Actually, I've just installed Chromium, and it seems to be quite a bit more responsive than Firefox. I'm just used to my FF extensions though...

Also, one other question - when I installed Ubuntu, this computer had 512mb ram in it. Since then I've managed to find another 512mb to put in it, so it's now got a gig. Do I need to increase my swap? It's only 478mb, and when I tried to hibernate last night it wouldn't do it and told me I didn't have enough swap space. How would I go about doing it?

One final question, for some reason when I suspend the computer, it never wakes up again properly, screen just stays black, keys and touchpad don't do anything, and I have to reboot. Is there anything I can do about this?

Late reply, I just happened to stumble on your post now. If by suspend you might actually mean hibernate, then your two issues are related. When you hibernate, the contents of the working memory are written to the swap space, from which it is then reloaded once you start up again. Having a swap size smaller than your RAM would therefore cause that not to work. I'm not sure exactly of the procedure for suspension, but I wouldn't rule out there being a correlation there either. Other than that, I don't think it's strictly necessary for you to have a bigger swap but with that low RAM, I'd take all the memory help I can get and increase it to 1 GB.

---

### Post by Kixtosh on 2011-09-29
> **anlag said:**
>  ... Having a swap size smaller than your RAM would therefore cause that not to work.  ...Anlag is correct. I would even increase the size to more than 1GB, maybe 1.5GB, or 2GB.

As for how to do it, if you are still wondering, you need to use the Live CD you used to install Ubuntu, and run GParted from there. Just increase the size of the swap partition (after deactivating swap, using GParted). If you are going to shrink any Windows partitions that you need to boot, to make room for the extra swap, make sure that you defragment using the Windows System tools first, about three times over (it goes faster each time you do it).

With those specifications, while performance might not be spectacular, it should be very good in my experience (with old laptops, that is), and you certainly shouldn't be experiencing one second typing lag.

I hope that anlag and myself are not too late to be of help.

---

