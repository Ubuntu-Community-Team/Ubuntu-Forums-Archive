---
title: "Uninstall Ubuntu for Lubuntu?"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by homebre973 on 2011-07-12
I probably need to uninstall Ubuntu to install Lubuntu because of old hardware?  If so how do I  uninstall Ubuntu or will Lubuntu just go on top of it?  I am running a duel boot system with windows XP, so I do  not want to play with partitions or reformat.  Thanks.
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                                                                                                                      [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=11039767")

---

### Post by Rex Bouwense on 2011-07-12
While I seldom try to talk anyone out of doing something, I have to make an exception here providing you are satisfied with Ubuntu.  Is Ubuntu running too slow for you then by all means install Lubuntu over Ubuntu.  However run it first from a live CD to insure that the hardware is compatible.  If you are happy with Ubuntu keep it.  Your choice.

---

### Post by MG&amp;TL on 2011-07-12
I've tried kubuntu, ubuntu, xubuntu, and I'm about to try lubuntu, and so far they've all had a 'install over' option. :)

Hope it helps.

---

### Post by sgadecki on 2011-07-12
I would do a clean install of Lubuntu (you should be able to  format your current Ubuntu partition during the install process).  You  won't have GNOME or most of  the GNOME apps but your 'old hardware' system will be faster.  You *can* install directly over the current Ubuntu, however I believe that leaves the existing GNOME and all the GNOME apps and all of their extra dependencies.  If you're not going to use GNOME or the GNOME apps, then that is just extra bloat.  Either way  Just as  Rex suggested, before installing, try out the LiveCD first and make sure  A)it works, and B)it's what you want.

---

### Post by snowpine on 2011-07-12
You don't need to reinstall. You can easily install lubuntu-desktop from the Software Center on your existing Ubuntu. :)

[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

---

### Post by homebre973 on 2011-07-12
> **Rex Bouwense said:**
> While I seldom try to talk anyone out of doing something, I have to make an exception here providing you are satisfied with Ubuntu.  Is Ubuntu running too slow for you then by all means install Lubuntu over Ubuntu.  However run it first from a live CD to insure that the hardware is compatible.  If you are happy with Ubuntu keep it.  Your choice.

Thanks.  I have run Ubuntu 11.0 even in classic mode with no effects and it works, but is very slow.

---

### Post by jerrrys on 2011-07-12
another thought

lubuntu will probally do the same, but i know in xubuntu you can also load the gnome desktop and choose which one to use.  also by loading this way, things like compiz and natty will not be loaded by default.  to me, this makes a nice setup...

---

### Post by nmaster on 2011-07-12
> **snowpine said:**
> 
[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)
+1

this is exactly what you need. psychocats will also help you switch to gnome, xfce, or kde. there are also guides on minimal installs (which would be even better for a lightweight system).

---

### Post by Rex Bouwense on 2011-07-12
Out of idle curiosity, does any one know if the Lubuntu applications are installed with this and the Ubuntu applications are uninstalled?

---

### Post by philinux on 2011-07-12
> **Rex Bouwense said:**
> Out of idle curiosity, does any one know if the Lubuntu applications are installed with this and the Ubuntu applications are uninstalled?

Yes and Ubuntu stays you just choose the session at login.

Have a look at the dependencies of lubuntu-desktop in synaptic ;)

---

### Post by mike555 on 2011-07-12
xubuntu 11.04 is very good and lighter, just much harder then Ubuntu to edit menu .......

---

### Post by mike555 on 2011-07-12
You could just try LXDE ,by installing "  LXDE-core " , it only installs the minimum to run LXDE ,and keeps your Gnome apps ...........

---

### Post by wildmanne39 on 2011-07-12
Hi, a couple of suggestions for your slowness with ubuntu, you might log out and into ubuntu with no effects and see if that fixes your problem, because compiz may be the issue, in classic with effects you need to revert compiz to the previous version for compatibility reasons, here is a link for that.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

Also you can run these commands in a terminal
```
/usr/lib/nux/unity_support_test -p
```
```
sudo lshw

```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets, if this information we can tell you if it is a hardware issue because of your system being to old.

---

### Post by whatthefunk on 2011-07-12
Id personally just burn a Lubuntu LiveCD and do a fresh install....

---

### Post by homebre973 on 2011-07-13
> **philinux said:**
> Yes and Ubuntu stays you just choose the session at login.

Have a look at the dependencies of lubuntu-desktop in synaptic ;)


Lubuntu worked much better for me.  Faster and clearer with my old XP machine.  Tha nks

---

