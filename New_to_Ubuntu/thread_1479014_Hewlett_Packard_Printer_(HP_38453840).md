---
title: "Hewlett Packard Printer (HP 3845/3840)"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by gemma.laming on 2010-05-10
Hi everyone,
I cannot get my printer to work.  I tried the forum where it said to install HPLIP, which I did.

That did not work.

That should not surprise me with my computer skills.  

Has anyone any ideas for me?  Or will this be another shout in the wilderness, unanswered as most of my posts are.

Fed up with Ubuntu - nice name: it's African like me - but that is all that is good about it.  

Gemz

---

### Post by ubunterooster on 2010-05-10
did you go to system>administration>printing?
Then on the "add" button?

Ubuntu is an African word meaning "I am who I am because of who we all are" but the common definition is "Humanity to others" to keep it simple

---

### Post by YuiDaoren on 2010-05-10
System --> Preferences --> HPLIP Toolbox

See if your printer is recognized there.

If it's not listed, then in HPLIP: Device --> Setup Device to start a "wizard" to help you get the printer set up.



<Am ignoring the Ubuntu-bashing for now>

---

### Post by ubunterooster on 2010-05-10
do you have the pakage "hplip-gui" ?

---

### Post by gemma.laming on 2010-05-11
Thankyou Ubunterooster and Yui Daoren, I appreciate your replies.  I will try your hints - but I will emphasize again that even the most simple things in Linux (such as installing a printer) can prove challenging to someone without serious quantities of computer knowledge.  

I did know about the meaning of Ubuntu - I still speak a modicum of Xhosa, I am South African - it is one reason why I chose the operating system.  I could wish it included me:-(

---

### Post by adam22 on 2010-05-11
I installed a wireless printer in 30 seconds in Ubuntu...it took over 15 minutes on Vista.

install the hplip and the hplip-gui via synaptic package manager. Then go to system>administration>printer>new>server>printer

If it's a network printer, just select that and you should see your device pop up, but I use manual discovery since my printer has a static IP.

If it's a USB printer the drivers should just install automatically.

---

### Post by ubunterooster on 2010-05-11
Yes, Adam,  but Ubuntu is far from perfect.

I have spent hors one day getting a printer to work when it worked fine the next day, and not at all the day following that. 

Notice both "should" clauses that you gave.

---

### Post by gemma.laming on 2010-05-11
Hi Adam,
it is nice of you to sort that information for me.

I did the bit with the HLIP or whatever it is, but I can't find how to do the "server/new" bit.

My printer is USB, and has "installed" automatically.  The only problem is that it doesn't work, and I can't find how to uninstall it to install it properly (or improperly once again?).

I am still using 9,03 (or is it 9,04?) I tried 9,10 but it was a disaster and I have no intention of leaving 9,03 until I have to!!

Any ideas any of you?  

I had the same problem as Rooster, I had a printer installed which worked ... and then didn't any more.  It was quite frustrating.  I can appreciate that with Microsoft it might take longer, but I guess it worked?

Thanks again guys Gemma

---

### Post by adam22 on 2010-05-11
I wasn't sure if this was a wireless printer or not...

If you disconnect the printer from the computer, you should still see it listed in the HPLIP menu but the device status will present a communication error. You are usually able to select the printer and click remove device. You can also right click and delete the device from the standard printing menu under System>Administration.

Reboot the computer, and try to set the printer up via the HPLIP program.

Here's a screenshot I took to show you what I am referring to...click to enlarge.

HPLIP Utility. Use this for HP Printers.
[[IMG]http://img546.imageshack.us/img546/3443/printer.th.png[/IMG]]("http://img546.imageshack.us/i/printer.png/")

Regular Printing Utility. Not needed if you have an HP device.
[[IMG]http://img208.imageshack.us/img208/5880/altprint.th.png[/IMG]]("http://img208.imageshack.us/i/altprint.png/")

You might find better help if you post in a different section, since this really isn't beginner talk. I'm not an expert, but I'll try to help.

---

### Post by gemma.laming on 2010-05-11
Thanks for the screenshots, Adam.  I have seen that sort of thing when trying to establish my printer, and it was never more than a "communication error".   I will see if your suggestions can prod my computer into recognizing my printer.  

If this gets me going - and I shall try this evening - I will be pleased.  As to posting this elsewhere, I have rarely strayed from this topic: Ubuntu at its easiest seems to be beyond my capabilities, so I shall stay here!
 Gem

---

### Post by gemma.laming on 2010-05-26
Hi Adam,
I'm sorry that it has taken this long to get back to you, but honestly I didn't try it until now ... why not?  Because it never worked in the past months of trying, and I did not expect it to work this time.  

However having discovered that the printer icon on the bar at the top was not in fact a printer at all, just a well out of date April fool from Ubuntu (a bit like the goldfish?  a stale and unappreciated joke).  I deleted that printer to find that the printer wasn't installed in the first place (so, please why the icon???!!).  I was not surprised by this as Ubuntu does its best to make life miserable for my computing life.  

I hope it works tomorrow as well.  

Gemma

Sick of Linux and wishing daily to have enough money for a mac.

---

### Post by gemma.laming on 2010-06-16
Dear All,
after a successful installation of my printer, on the second time of using it - of course it fails to work.  It is to be expected in Ubuntu as my printers have always worked once, and once only.  

I am so truly fed up of this operating system.  I used to like the sound of the singing at the start, but now it is just a reminder that I am tied to a computer that does not do what I need it to.

Gemma :-(

---

