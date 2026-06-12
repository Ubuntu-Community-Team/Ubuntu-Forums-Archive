---
title: "Linksys WMP11 works in Freespire, why not ubuntu?"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Tesgin on 2007-02-12
I just installed ubuntu on a stable computer, several years old.  Works great, EXCEPT I cannot get my Linksys wmp11 wireless pci card working.  I've perused the forums, but no luck.

I also did a test drive of Freespire, and it works there without a hitch.  no configuring at all.  CANNOT get it to work in ubuntu.

Can someone help me with this?  Is it possible to get the driver somehow out of the freespire set up?  I just ran that from a live cd.

I'm a total newbie.  Very conversant with XP (though I hate it), but know nothing about ubuntu.

Thanks in advance,
Tesgin

---

### Post by Metaljaz on 2007-02-13
type this command from the terminal window:

lspci

look for network controller
once you find it you should see the card name and chipset 
once you know the chipset do a search for the drivers.
If unsure cut and paste the results of lspci here.

you will probably have to use the windows drivers and ndiswrapper

---

### Post by Tesgin on 2007-02-13
Thanks.
lspci tells me it's a bcm4303 chipset.  My card is a wmp11 v. 1.0 (not the v. 2.7 on the wiki list).  But, since lspci is listing it, can I assume the driver and firmware are loaded?  Is it maybe just a matter of properly configuring it?

Following the sourceforge instructions, I've learned that the PCI ID of the card is 14e4:4301 (rev 02).

I'm not really sure where to go next?

TB

---

### Post by gradedcheese on 2007-02-14
Broadcom has a terrible (non-existant?) track record with Linux.  The bcm4303 chipset, as far as I know, is not supported in any way because Broadcom won't work with the community or release any documentation to enable a driver to be written.

You can make it work via ndiswrapper, a wrapper that allows the Windows driver to support the card.  Because Linspire has a very loose stance on proprietary drivers, I would guess it shipped out of the box with this already set up.  However you can do the same in Ubuntu, just follow an ubuntu ndiswrapper install guide (there are several here) and use that to install the driver.  Remember to "sudo modprobe ndiswrapper" when you are done and "sudo /etc/init.d/networking restart"

There's also this petition to sign, but I am not sure it's going to work:
[http://www.petitiononline.com/BCM4301/petition.html](http://www.petitiononline.com/BCM4301/petition.html)

---

### Post by Metaljaz on 2007-02-14
ok, now try this wiki:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

pick the version of Ubuntu that you are using and give it a try.

---

### Post by Tesgin on 2007-02-17
Boy, I'm sorry, I'm really trying, but this is so confusing.  Reading these instructions is like an unfamiliar foreign language to me.

Here's what I've got so far:
First off, I was wrong:  my card is a wmp11 v.2.7 (NOT v.1 as I originally thought).
From the SourceForge wiki and using lspci, I learn that my PCI ID is 14e4:4301 (rev 02).
I went to the wiki list and downloaded the driver (OR, I've also downloaded the driver from Linksys's website).
I used winzip to extract the .exe file on my laptop to isolate the driver, which is a file named bcmwl5.inf.

Now, I'm confused.  The Linux How To guide says my card is not compatible with Linux ([HERE]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Configuring_Linux_with_Incompatible_Wireless_NICs")), but other sites ([HERE]("http://bcm43xx.berlios.de/?go=devices")) say it IS supported.

I don't know if I should try to install the firmware using the fwcutter program referred to in the [LinuxHomeNetworking Wiki]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Configuring_Linux_with_Incompatible_Wireless_NICs"), or just use ndiswrapper.

I don't know how to use fwcutter, cuz I can't download it, cuz my computer isn't connected to the internet (cuz my CARD doesn't work!!).  Or do I not need to do that cuz I've already isolated the driver using winzip on my laptop?

OR, if I use ndiswrapper, I don't understand how to do it.  I did transport the file,  bcmwl5.inf, to my Linux Ubuntu machine via a usb flash drive.  I put it on the desktop, opened the terminal and tried ndiswrapper -i bcmwl5.inf.  Didn't work.  I got an error message saying "unable to create directory /etc/ndiswrapper/bcmwl5.   Make sure you are running as root."

I KNOW I'm not doing it right.  I'm absolutely lost.

HELP!

Thanks in advance,
Tesgin

---

### Post by teet on 2007-02-17
Prepare to be even more confused....

I have the same card that you have.  It will work great with dapper, but you're going to run into some problems on edgy if you use the fwcutter solution (i.e. not ndiswrapper).  Here is what I've encountered.

Fwcutter solution:  This is what I am currently using on my edgy box.  The card works but there is this really annoying bug that causes random lockups.  Basically, after I've been booted for 0-12 hours something will mess up and my keyboard will not work anymore.  I will have to do a hard reboot.  The problem is outline here ( [http://ubuntuforums.org/showthread.php?t=314614](http://ubuntuforums.org/showthread.php?t=314614) ).  Apparently there is some "glitch" with the kernel, but this "glitch" has already been fixed in newer kernel versions (but you can't get these newer versions unless you want to do it manually in edgy).

Ndiswrapper Solution:  I tried this the other day and got the driver installed and everything, but my network-manager wouldn't actually connect to my home network.  The name showed up and everything, but it wouldn't work.  I quickly reverted back to the fwcutter solution.

So, here are the options that you have:

1.  Use the fwcutter solution with edgy and endure random lockups (I only use my desktop for 2-4 hours in the evening anyway so it doesn't really bother me much).
2.  Revert back to dapper where the fwcutter solution works flawlessly.
3.  Cross your fingers and try out the next ubuntu release (Feisty Fawn)
4.  Figure out how to get ndiswrapper to work correctly.
5.  Buy a new wireless card with native linux support.

-teet

Edit:  To use the fwcutter solution I had to use my laptop to download the files.  I used 

```
sudo apt-get install -d blah
``` 

to download the packages.  It will download the packages to /var/cache/apt/archives.  I then manually transferred the packages I needed to my flash-disk, copied them to my desktop, and installed the *.deb packages.  It was a bit of a chore, but you got to do what you got to do.

---

### Post by Tesgin on 2007-02-18
Thanks, Teet.  Very helpful.

It sounds like you downloaded fwcutter to a laptop with ubuntu on it?  My laptop has XP Home on it.  What do I need to do to get the fwcutter program onto my ubuntu pc?  

Similarly, if I do try ndiswrapper, can you explain to me what I did wrong?  I just don't get it.

Thanks in advance,
Tesgin

---

### Post by teet on 2007-02-18
> **Tesgin said:**
> Thanks, Teet.  Very helpful.

It sounds like you downloaded fwcutter to a laptop with ubuntu on it?  My laptop has XP Home on it.  What do I need to do to get the fwcutter program onto my ubuntu pc?  

Similarly, if I do try ndiswrapper, can you explain to me what I did wrong?  I just don't get it.

Thanks in advance,
Tesgin

The error message you got about not running as root is easy to fix...

Just add "sudo" in front of the commands (it stands for "superuser do" if you were wondering).  For instance, typing 'sudo ndiswrapper -i blah.inf' would install the blah.inf file in ndiswrapper.  

Are you sure you're using the correct *.inf file?  The 2 *.inf files I have are called "WMP11V27.inf" and "WMP11NDS.inf"

-teet

---

### Post by Tesgin on 2007-02-18
Okay, I'll try that, and post back

_Two_ .inf files?  I only have one.  And, yes, it does have a different name.  I downloaded mine from the wiki list.

Now I do have a driver file I also downloaded from the Linksys website.  THAT one does appear to have the two .inf files you mentioned.  If I were to use that, which of the two .inf files would I use?

Thanks,
Tesgin

---

### Post by Tesgin on 2007-02-18
A follow up...

I did try running ndiswrapper as you suggested.

sudo dkiswrapper -i bcmwl5.inf

I got the following:

Password: (entered)
Installing bcmwl5
couldn't copy bcmwl5.inf at /usr/sbin/ndiswrapper -1.8 line 144.

Any thoughts?

Tesgin

---

### Post by Tesgin on 2007-02-18
And one more followup:

ndiswrapper -l now says:

Installed drivers:
bcmwl5 invalid driver!

Is there something now that I need to do to get the bcmwl5 driver OUT of there?

So confusing...

TB

---

### Post by teet on 2007-02-18
To remove a driver just type

sudo ndiswrapper -r bcmwl5
or
sudo ndiswrapper -r bcmwl5.inf

I can't remember which one.

I think you need to use WMP11V27.inf

If it doesn't work, you can easily remove it and install the other one :)

-teet

---

### Post by Tesgin on 2007-02-18
Teet,

Still having problems.

I did sudo ndiswrapper -i wmp11v27.inf, and got the following:
Installing wmp11v27
coudn't copy wmp11v27.inf /usr/sbin/ndiswrapper-1.8 lin 144.

I did sudo ndiswrapper -l, and it says
Installed divers:
wmp11v27.inf invalid driver!

---

### Post by teet on 2007-02-18
Hmmmm...not sure what the problem is.

Try removing the old stuff 

```

sudo ndiswrapper -r wmp11v27
sudo ndiswrapper -r wmp11v27.inf

```

Then you can try grabbing my *.inf files from here:

[http://www.missouri.edu/~datcnc/wireless](http://www.missouri.edu/~datcnc/wireless)

and giving them a go.

Also remember that linux is case sensitive...in other words capitalization matters!  WMP11V27.inf is different from wmp11v27.inf

Also, I uploaded the *.deb packages I used to install fwcutter and network-manager in edgy.  They probably aren't the latest, but they should work if you want to try the "fwcutter solution".  at a command line just type:

```

sudo dpkg -i blah.deb

```

to install

-teet

---

### Post by Tesgin on 2007-02-18
Thanks, Teet.  

I downloaded your files (THANK YOU!), but am still getting that same error message:
coudn't copy wmp11v27.inf /usr/sbin/ndiswrapper-1.8 lin 144

Then when I do ndiswrapper -l, it says it's an invalid driver.  I just don't get it.

I installed the fwcutter thing as well.  I tried the instructions from [this site]("http://ubuntuforums.org/showthread.php?t=185174"), and downloaded the driver file wl_apsta.o from that site as well, and then ran:

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o

But that didn't work either.  It gave me error messages about the driver being too old.

If I were to run this with the drivers I downloaded from your site, can you help me with the commands?

TB

---

### Post by mlnease on 2007-11-10
Hi Tegin,

Check this out--no Ndiswrapper necessary (many thanks to Tom Adelstein):  [http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

It worked great for me in Ubuntu 6.06.1, if it works for you please help spread the word.

Cheers,

mlnease

---

