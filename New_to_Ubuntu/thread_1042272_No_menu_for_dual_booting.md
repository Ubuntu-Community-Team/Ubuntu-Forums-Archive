---
title: "No menu for dual booting"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by OllieGab on 2009-01-17
I've got Ubuntu as my main OS and I also had OpenSuse installed in a different partition. This workded fine; always asked what OS I wanted to boot.

Now I've installed Fedora 10 **instead** of OpenSuse. Installation went okay, OS working fine. But I don't get the choice now whether to boot up my Ubuntu or my Fedora. It automatically boots Fedora.

So how do I boot up my Ubuntu now? I assume it's got to do with 'grub', but as I'm very new to Linux I don't really know where to go from here!!!

Ollie

---

### Post by seagullplayer77 on 2009-01-17
You might try editing /boot/grub/menu.lst. My guess is that Fedora may have changed the Grub configrution file and that Grub may be set to boot Fedora automatically now. 

Check out this line:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout	4
```

Maybe the timeout is set to 0? If that was the case, it would automatically boot the default OS without every displaying the Grub menu.

Just a thought...but my best bet is that the problem lies somewhere in menu.lst.

---

### Post by seagullplayer77 on 2009-01-17
Here's another idea...

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

If the last line of code isn't commented (doesn't have a number sign in front of it), then the Grub menu won't show up unless you press "Esc." You might want to check out that line as well.

If you could post your entire /boot/grub/menu.lst, that would probably be helpful.

---

### Post by OllieGab on 2009-01-17
Looking in the menu.1st file (when i Fedora obviously as that is the only one I can access right now) I get an error message: "Could not display "/boot...." There is no application installed for this fily type"

Ollie

---

### Post by seagullplayer77 on 2009-01-17
That seems rather odd...

Try running this:

```
sudo pico /boot/grub/menu.lst
```

In a terminal window. If that doesn't get you something, then there's definitely something fishy going on.

Btw, it isn't menu.**1**st, but menu.**L**st...I guess the text can be kind of hard to read at times :P.

---

### Post by jimmy the saint on 2009-01-17
How about showing us the contents of the /boot/grub/menu.lst.
Wrap them in code tags so the post is not so long.

---

### Post by OllieGab on 2009-01-17
When it rains, it pours....

Any sudo command will now give me "usr is not in the sudoers file..."
That's never happened to me before. I've only ever used one password for any prompt that comes up when installing (the same I use for logging on) so why it would it suddenly not recognise my user name...?

It accepts it in other GUI related requests...

---

### Post by jinkydondon on 2009-01-17
I using ubuntu 8 for my os and I installed new hard drive with windows in it from my old computer. How can i make my windows as my os ????

---

### Post by caljohnsmith on 2009-01-17
OllieGab, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, and then do the following as **root user**, but replace <username> with your username:
```
bash /home/[COLOR="Blue"]<username>[/COLOR]/Desktop/boot_info_script*.sh
```
To become root user, I think you can do either "su" or "su -" at the command line. But the above script will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by seagullplayer77 on 2009-01-17
> **OllieGab said:**
> When it rains, it pours....

Any sudo command will now give me "usr is not in the sudoers file..."
That's never happened to me before. I've only ever used one password for any prompt that comes up when installing (the same I use for logging on) so why it would it suddenly not recognise my user name...?

It accepts it in other GUI related requests...

That's an interesting development, and unfortunately, one that's beyond my experience to address. Here's a wild, crazy idea that may not work at all, but it might be worth a try.

Try running the same command from a shell (Ctrl + Alt + F1) and see if it gives you the same error with sudo. While you won't be able to copy the text of /boot/grub/menu.lst easily from the shell, you should be able to edit it (assuming that it'll accept the sudo command, of course) and get your Ubuntu partition back up and running.

---

### Post by OllieGab on 2009-01-17
Well, that is sort of the problem. I downloaded the script but as I try to use it I get the same message, saying I'm not in the sudoers file.

I did "re-install" Fedora, and at one point it asks me whether I want to install the boot loader. I have a feeling that this has something to do with it. I actually added an item to the boot loader and now I get a menu when starting the PC up.
If I choose Ubuntu (which is only called that because I told it that, and that I believe that Ubuntu is located there) the PC just go quiet and nothing happens.
I obviously do something wrong, but maybe I'm on the right track?

---

### Post by Elfy on 2009-01-17
Let fedora write it's bootloader to it's own partition.

Reinstall buntu's grub with the livecd and chainload fedora it's what I did 

[http://ubuntuforums.org/showpost.php?p=4542943&postcount=2](http://ubuntuforums.org/showpost.php?p=4542943&postcount=2) to reinstall grub.

We'll need to deal with the sudo problem seperately.

---

### Post by caljohnsmith on 2009-01-17
OllieGab, I may be mistaken, but I don't think Fedora has sudo enabled. That means if you want to run something as root, try switching to the root user by doing either of the following:
```
su
su -
```
One of those should work if I remember correctly.

---

### Post by Elfy on 2009-01-17
Yes you're right in fedora use su - give root password.

[http://docs.fedoraproject.org/fedora-install-guide-en/fc4/ch-bootloader.html](http://docs.fedoraproject.org/fedora-install-guide-en/fc4/ch-bootloader.html)
[http://docs.fedoraproject.org/fedora-install-guide-en/fc4/sn-bootloader-advanced.html](http://docs.fedoraproject.org/fedora-install-guide-en/fc4/sn-bootloader-advanced.html)

All that aside, try to reinstall your ubuntu grub

Then add a chainloader for fedora

> title		--Fedora--
root		(hdx,y)
chainloader	+1

You will need to get the correct partition information for your fedora install to replace (hdx,y).

---

### Post by OllieGab on 2009-01-17
That worked fine!
Well, I can't boot Fedora now but that seems less important. I just wanted to try it out, which I have a live CD to do.

I'll probably try something else soon and then I'll have other - but similar problems - but for now I'm happy!

But just out of interest; if I wanted Fedora back I'd more than likely have the same problem again, so how does the grub work? Is it one grub file for each system? If so, where does the dual boot menu come in?

I've tried 2-3 different distros like this, together with the Ubuntu but I haven't had this problem before.

Cheers everyone!

---

### Post by Elfy on 2009-01-17
It's still there I assume so just get the partitions and add it to the boot menu.

---

