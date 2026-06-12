---
title: "Red Box DVD's, Spoofed MAC and 'jails' ?"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by zipteye on 2010-12-06
Four quick questions. (For the price of one!)
 
1) My Meerkat doesnt pick up redbox dvd's and play them. Is there a fix for this?
 
2) In the spoofed MAC address option, can I put just any old characters in there or does it have to model the same format as the real MAC address?
 
3) If something nefarious is picked up on my ubuntu partition, can it run amok on the entire hard drive or is it contained to the Ubuntu partition?
I assume that if the evil seed is running under my permissions (Admin) that it can run through the whole HD.
Any way to "Jail" , or "box in" what happens within the Ubuntu partition?
You know, "What happens in Ubuntu stays in Ubuntu".
 
Can we make the old, "My wireless USB device isn't picking up the network" question, from dual boot windows users, a Sticky?
 
Step one:
Install ndiswrapper
 
Step two:
Use the 32 bit drivers. Windows XP. (64 no workey)
 
Step three:
ndiswrapper -i "theinfFile".inf
 
Step four:
sudo gedit /etc/modules
 
lp
ndiswrapper
 
(save it)
 
Step five: Reboot.

---

### Post by zipteye on 2010-12-06
Bumpity

---

### Post by CharlesA on 2010-12-06
1) Install ubuntu-restricted-extras, that'll allow you to play dvds.
2) Why bother spoofing yer mac address? It's transmitted with every packet you send wirelessly.
3) It would be confined to the Ubuntu partition (and more then likely, your home directory)

---

### Post by anewguy on 2010-12-06
And.....why go to the trouble of command-line ndiswrapper when it's simpler with the GUI front-end ndisgtk?  Also, you are making it WAY to generic - a LOT of adapters require updating other files - including the blacklist.conf file.  Combine that with the idea that there are literally THOUSANDS of posts on the forum, many unique to a particular adapter, and the information is already here.  Your example doesn't cover most adapters, leaves open the possibility of errors due to command line typing and editing, and is easily out-run by ndisgtk.  Ndisgtk takes care of everything you posted and more.

Now, let's also go a step further.  A lot of the adapters that used to require ndiswrapper/ndisgtk no longer require that.  There is a LOT of material out there that is old and outdated.  You didn't mention looking in Additional Drivers to see if a driver is there.  You didn't mention connecting via hardwire if possible, doing a sudo apt-get update, then checking Additional Drivers again.

you are making something way too simple - it may be based on your experience, but it is limited.

Another example - ndiswrapper, ndisgtk are both on the installation CD.  So is a method you skipped - b43-firmwarecutter.

Too generic to do much good - people are going to post back with questions and problems from those instructions.

Not trying to cut you down or your suggestion, it's just that there is a LOT more to it than that.

Also - please note that the forum rules dictate waiting 24 hours for a reply before bumping a thread.

Dave ;)

---

### Post by zipteye on 2010-12-07
> **anewguy said:**
> And.....why go to the trouble of command-line ndiswrapper when it's simpler with the GUI front-end ndisgtk?  Also, you are making it WAY to generic - a LOT of adapters require updating other files - including the blacklist.conf file.  Combine that with the idea that there are literally THOUSANDS of posts on the forum, many unique to a particular adapter, and the information is already here.  Your example doesn't cover most adapters, leaves open the possibility of errors due to command line typing and editing, and is easily out-run by ndisgtk.  Ndisgtk takes care of everything you posted and more.

Now, let's also go a step further.  A lot of the adapters that used to require ndiswrapper/ndisgtk no longer require that.  There is a LOT of material out there that is old and outdated.  You didn't mention looking in Additional Drivers to see if a driver is there.  You didn't mention connecting via hardwire if possible, doing a sudo apt-get update, then checking Additional Drivers again.

you are making something way too simple - it may be based on your experience, but it is limited.

Another example - ndiswrapper, ndisgtk are both on the installation CD.  So is a method you skipped - b43-firmwarecutter.

Too generic to do much good - people are going to post back with questions and problems from those instructions.

Not trying to cut you down or your suggestion, it's just that there is a LOT more to it than that.

Also - please note that the forum rules dictate waiting 24 hours for a reply before bumping a thread.

Dave ;)

Never even read the forum rules.  :KS

Ok, my list is too simple and too generic, but there must be a commonality among all of these wireless issues. At least for the USB wireless adapter issues.

I'm new, that is true, and I may be stepping in and giving my two cents when i should just wait and read, but... I've noticed a tendency for some posts to make things way too complicated for the 'brand new guy'.
Maybe a general help outline using a sort of upside down funnel approach.
Start very simple and generic, then expand outward in detail and complexity until the issue is solved.

```

     -
    ---
   -----
  -------

```

---

### Post by zipteye on 2010-12-07
> **CharlesA said:**
> 1) Install ubuntu-restricted-extras, that'll allow you to play dvds.
2) Why bother spoofing yer mac address? It's transmitted with every packet you send wirelessly.
3) It would be confined to the Ubuntu partition (and more then likely, your home directory)

2) I'm sorry. The 'Cloned MAC address' option in network settings.
That's what I was wondering about.

---

### Post by anewguy on 2010-12-07
Unfortunately there really is no commonality between adapters, be they internal or external.

As an example, some are just plug and play but the new user doesn't know it.  Others can use "restricted" or native drivers, but may require a modprobe of a driver module and subsequent editing of the modules file.  Others may require loading a driver source file, making it and loading the resultant module(s).  Others go even further (see the list of my posts and you'll see a current one), requiriing loading the driver source, making it, loading WPA support source, making it, loading the resultant modules, editing a file to configure WPA, using supplied scripts for bringing the network up or taking the network down.  While rare, some go so far as to require compiling the kernel, at least from what I've seen.

When starting to provide an answer to what driver to get, we either go by what is provided by lsusb, if it shows a chipset, or by the manufacturer id and product id from lsusb -> the xxxx:yyyy part.  Most of the time the chipset is not the same as the manufacturer of the adapter, so the user is confused and says "I have adapter 'X'" even when we tell them they need the driver for chipset 'Y'. 

I guess what I'm getting at is that the permutations can get horrific.  You need trees for each adapter manufacturer.  Within that tree you need trees for each model.  Within those trees you often need trees for varying chipsets used by the manufacturer for different version numbers even though the adapter is still known as 'X'.  Then you need the individual instructions per model/chipset.

I hope you can see what I'm getting at.  While it would be nice to be able to go by chipset, which is much more limited than manufacture/model/version combinations, the truth of the matter is people don't know (and why should they?) squat about a chipset on their adapter - they just know they bought adapter 'X'.

Please understand the last thing I'm trying to do is cut you down - far from it!  I may have a few more beans in my counter, but they don't mean squat.  I'm constantly learning more and more, and the above are just my observations from personal experience and trying to help on the forums.

You can already find some help web pages for varying chipsets, etc..  They just are not always easy to find.

Please - continue with your enthusiasm - it is always needed!  If you think you are up to the challenge, contact one of the forum moderators and ask how you can get started and see if you can get others to form a team of contributors.  Just be ready for the questions to still continue, the "I read it but I don't get it" to continue.  It's just the nature of the beast.

All the best!

Dave ;)

---

### Post by aeiah on 2010-12-07
MAC addresses are in hexadecimal, that is 0-9, a-f (16 digits). there are genuine reasons for spoofing or cloning a mac address. some ISPs only allow one computer to connect (this is pretty rare nowadays though) and identify it through the mac address. also, some routers dont like wireless bridges, and cloning the mac address so the bridge has the same MAC as the connected client can get around this. also, you may have firewall rules set up based on a MAC address, so you may want your ethernet MAC to be the same as your wireless MAC so you can easily have the same rule set.

there are also more crafty reasons, such as connecting to a wireless access point that only allows MAC addresses that are on a whitelist, or to cover your tracks if you're infiltrating someone elses network.


as for something nefarious on your ubuntu partition.. if you grant root access to a program, then it can do anything to all partitions. normally most software runs as your user, and so can only do things your user can do (without the 'sudo' command) ie, it can delete non-system files etc. there isnt really any known malware for linux out there so you shouldnt have a problem.

what i suspect you're actually asking is "if i get a windows virus whilst in ubuntu, can it do damage?" and the answer is no, because windows software can't execute on linux.

---

### Post by CharlesA on 2010-12-07
> **zipteye said:**
> 2) I'm sorry. The 'Cloned MAC address' option in network settings.
That's what I was wondering about.

Where are you looking?

That's not normally used normally.

---

### Post by zipteye on 2010-12-07
> **CharlesA said:**
> Where are you looking?

That's not normally used normally.

System > Preferences > Network Connections > Wireless

---

### Post by zipteye on 2010-12-07
Thanks Dave:-)

---

### Post by anewguy on 2010-12-07
> **zipteye said:**
> Thanks Dave:-)

You're welcome, and thanks for understanding that there are no personal attacks, etc., intended at all!!

Glad you're aboard the ubuntu train!!

Have a good one!

Dave ;)

---

### Post by CharlesA on 2010-12-07
> **zipteye said:**
> System > Preferences > Network Connections > Wireless
Ah that explains it. I've not bothered with it in any case, as it's not really needed.

---

### Post by hdemarzo on 2010-12-07
Yeah, in order to play ANY dvd's you need the extras, and the libcss that is under the ppa install.  Just google "ubuntu restriced extras"  an you will get the main site link.

---

### Post by QLee on 2010-12-07
> Originally Posted by **zipteye**                  
                 [I]2) I'm sorry. The 'Cloned MAC address' option in network settings.
That's what I was wondering about.[/I]
[QUOTE=CharlesA]Ah that explains it. I've not bothered with it in any case, as it's not really needed.[/QUOTE]

I agree that it's not really needed. If you enter the correct one for your interface, it can make your connection marginally faster because the Gateway/Router then doesn't have to resolve it. But marginally means just that, I don't bother with it either.

[Edit] by "connection" I mean initial connection time, not ongoing connection speed.

---

