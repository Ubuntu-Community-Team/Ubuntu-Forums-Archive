---
title: "Avast won't install properly ??"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by chris301up on 2011-07-13
You may have read in my previous threads that I was unable to maintain connection to the internet via my Linksys wireless card - but hopefully this is now sorted??

I just have one other issue. I thought I would install Avast Anti-Virus, as a matter of course, but when I now try to open the program I get the following message [COLOR="Red"]**"An error occurred in avast!engine. Invalid argument!"**[/COLOR]

Does anyone know what the problem is?

---

### Post by mastablasta on 2011-07-13
what commands are you using to install it?
 
i hope you are using the linux version of the AV...

---

### Post by Mark Phelps on 2011-07-13
Why are you even bothering with AV products? Linux distros don't need them.

If you're doing this to try to run AV against MS Windows partitions (in a dual-boot setup), you would actually do better going to the Kaspersky site, downloading and burning their Rescue CD, booting from that -- and running AV against MS Windows that way.

---

### Post by gandaran on 2011-07-13
you can find the fix to the problem on the second thread from the search results.
[http://ubuntuforums.org/search.php?searchid=81961390](http://ubuntuforums.org/search.php?searchid=81961390)

---

### Post by chris301up on 2011-07-13
I am using Avast4Workstation-1.3.0-1.586.rpm downloaded from the Linux web site and then I used the package installer within Ubuntu.

I realise anti-virus software is not absolutely necessary but would prefer it installed for peace of mind.

I do not wish to have a dual-boot system and would therefore like to know what the problem with this program is?

---

### Post by Swagman on 2011-07-13
> Avast4Workstation-1.3.0-1.586**.rpm**

The bold bit is your issue

Your trying to run a package for RedHat (.rpm) on a Debian (.deb) based system

I'm pretty sure there is a .deb option available if not the you will have to install alien to convert rpm's to .deb's

[edit]

Ok, after some googling (NOT Binging) I went to avasts site and...[http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

This link for a **.deb**

[http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb) <---

 As you appear to be unaware... Ubuntu is based on the Debian branch of Linux

Debian is pronounced Deb-Ian 

Deb being Debbie, Ians girlfriend (Now wife)

---

### Post by bennyroger on 2011-07-13
If they don't have deb tar files can be used but they are a bit more complicated to install for beginners.

---

### Post by dcsoldschool53 on 2011-07-13
For results from those who know, you should have gone here. ```
[http://forum.avast.com/index.php?PHPSESSID=9uhjfv1mln63a51jum48qdgvj7&board=5.0](http://forum.avast.com/index.php?PHPSESSID=9uhjfv1mln63a51jum48qdgvj7&board=5.0)
``` Avast has it own forum. I am sure you could have found your answer there.

---

