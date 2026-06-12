---
title: "Cannot update after freeze during update install"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by fathumthis on 2009-11-12
I spoke too soon..... I commented that these freezes would not be a problem to me as I dont do anything important with my laptop :-).
Recently installed 9.04 (dual boot with XP on a Fujitsu Siemens amilo pro 5 year old laptop) freezes are apparently random and vary in frequency.
I had a freeze during an update install and now I cannot update or search and install Packages!

I get an error message " E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. "

where can I find out how to do this and is it complicated?

much appreciate any help, first with this problem and after with the freezes that caused it :-)

---

### Post by philinux on 2009-11-12
Apps>accessories>terminal. Copy and paste the command below, hit enter, sit back while it sorts itself out.

```
sudo dpkg --configure -a
```

---

### Post by fathumthis on 2009-11-14
Thank you for that Philinux :-). I paste the result below as it mentions ***errors were encountered*** at the end! I haven't tried it yet but if I do then maybe I don't have the result below to forward for help. I will come back with an answer now.....


Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up cups-common (1.3.9-17ubuntu3.4) ...
Setting up libcups2 (1.3.9-17ubuntu3.4) ...

Processing triggers for ufw ...
dpkg: error processing cups-bsd (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libcupsimage2 (1.3.9-17ubuntu3.4) ...

Setting up cups (1.3.9-17ubuntu3.4) ...
 * Reloading AppArmor profiles ...                                       [ OK ] 
 * Starting Common Unix Printing System: cupsd                           [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cups-bsd

---

### Post by fathumthis on 2009-11-14
I tried the update and this time it tells me [B]*You have 1 broken package on your system! Use"Broken" filter to locate it*
[/B]It did, however, install all the updates shown which is great thanks

:redface: at the expense of sounding unable to do anything for myself, Where do I find the "Broken" filter ??? :)

---

### Post by jmszr on 2009-11-14
fathumthis,

Go to the Synaptic Package Manager (System > Administration > Synaptic Package Manager). In the lower left select "Custom Filters", then in the left pane select "Broken". Check the package that appears on the right and remove it.

Hope that helps.

---

### Post by WitchCraft on 2009-11-14
On the console, try:
```

apt-get upgrade

```

apart fromt the error you get, you see which package is broken.

Then use
```

apt-get remove --purge <packagename>

```

---

### Post by fathumthis on 2009-11-14
> **jmszr said:**
> fathumthis,

Go to the Synaptic Package Manager (System > Administration > Synaptic Package Manager). In the lower left select "Custom Filters", then in the left pane select "Broken". Check the package that appears on the right and remove it.

Hope that helps.


Thanks jmszr
that was easy but there was nothing to find in the right and so maybe the install was completed and fixed (or finished from the point where it previously froze during the download?!).

So all is ok now but for the freezes.:)

---

### Post by fathumthis on 2009-11-14
> **WitchCraft said:**
> On the console, try:
```

apt-get upgrade

```apart fromt the error you get, you see which package is broken.

Then use
```

apt-get remove --purge <packagename>

```


Thanks for the suggestion WitchCraft but I have to say, as a beginner, that command line / console worries me and I will always try any other available option first. Just for my info though, if I did try your method,

 would I include the[COLOR=Red] <   >[/COLOR] as in the example or just the packagename without them

 and also

 when I see a space is it reasonable to assume that it is a single space (sometimes I worry too much)

---

### Post by WitchCraft on 2009-11-15
> **fathumthis said:**
> Thanks for the suggestion WitchCraft but I have to say, as a beginner, that command line / console worries me and I will always try any other available option first. Just for my info though, if I did try your method,

 would I include the[COLOR=Red] <   >[/COLOR] as in the example or just the packagename without them

 and also

 when I see a space is it reasonable to assume that it is a single space (sometimes I worry too much)

Without the angle brackets, with as much whitespaces as you want, as long as it is at least one.

I would learn the console way, it's a lot faster than the graphical interface, you can just copy paste all the commands.

Use sudo in front of apt-get, unless you run as root, which is not recommended.

In your case, open gnome-terminal and try:
```

sudo apt-get remove --purge cups-bsd

```

Afterewards,you can reinstall that package:
```

sudo apt-get install cups-bsd

```

---

### Post by fathumthis on 2009-11-17
that worked easy as pie thanks and I did what it suggested and autoremoved the stuff it installed for that operation too :-)

when you sent the original suggestion you did not use the '**sudo**';
Quote;
 					*Originally Posted by **WitchCraft** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8313870#post8313870")* 				
 				[I]On the console, try:

[/I] 	*Code:*
 	*apt-get upgrade* 
[I]apart from the error you get, you see which package is broken.

Then use
[/I]   	*Code:*
 	*apt-get remove --purge <packagename>* 
Does the **sudo** build in some safety for me as it warns the system it is dealing with and amatuer :-)

I dont know why but I cannot 'Ctrl C' to copy but this is OK for short commands 

Thanks for your help

---

