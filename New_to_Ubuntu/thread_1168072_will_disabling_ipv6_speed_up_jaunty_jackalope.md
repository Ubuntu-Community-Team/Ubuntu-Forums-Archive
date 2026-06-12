---
title: "will disabling ipv6 speed up jaunty jackalope?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by djmh on 2009-05-23
i have seen a lot of posts on this,but they were all older so i didn't know if it is still relevant
and if i do do it,is there anything i should be ware of?
anything that will not work as a result etc etc.

---

### Post by blueridgedog on 2009-05-24
There are many threads that imply it will speed up your Internet access, IF your router does not understand ipv6.  Since the changes can easily be undone, it is a simple thing to test.  I just removed the ipv6 module in my setup and I will see if I think it performs better.

---

### Post by blueridgedog on 2009-05-24
OK, after disabling ipv6 I THINK things are slightly faster...though I have no logical way to verify it.  I will try it for a few days.

---

### Post by mrbiggbrain on 2009-05-24
open

```
# vi /etc/modprobe.d/aliases
```

and edit the line

```
alias net-pf-10 ipv6
```

to
```

alias net-pf-10 off
alias ipv6 off
```

[source ]("http://www.cyberciti.biz/tips/linux-how-to-disable-the-ipv6-protocol.html")

and probably the easiest way to tell if there is a change is to do a ping test

---

### Post by blueridgedog on 2009-05-25
I ended up commenting out the one line and then adding the new ones, as such:

```

#alias net-pf-10 ipv6
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off 
```

Then either reboot or pull the module while networking is stopped:

```
sudo /etc/inet.d/networking stop
sudo modprobe -r ipv6
Make your changes to aliases now.....
sudo depmod -a
sudo /etc/inet.d/networking start 
```

---

### Post by binbash on 2009-05-25
Those are not for jaunty.Read this blog post to disable ipv6 :

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

### Post by blueridgedog on 2009-05-25
Ouch.  So it is not a module now.  I suspect that it is not worth the fight then.

---

### Post by 73ckn797 on 2009-05-25
There are tweaks you can find that will make a noticeable difference in Firefox. Check out this link that I have used many times:
[http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx](http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx)

---

### Post by sdowney717 on 2009-05-25
test out the Google Chromium browser in Alpha and see how fast it is. 
for me loads 100% faster than firefox. Everyone is noticing how fast it is.

---

### Post by binbash on 2009-05-26
> **sdowney717 said:**
> test out the Google Chromium browser in Alpha and see how fast it is. 
for me loads 100% faster than firefox. Everyone is noticing how fast it is.

Because there are no features and plugins at chromium and it is not Google Chrome, it is Chromium :)

---

### Post by egalvan on 2009-05-26
> **73ckn797 said:**
> There are tweaks you can find that will make a noticeable difference in Firefox. Check out this link that I have used many times:
[http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx](http://codebetter.com/blogs/darrell.norton/archive/2005/01/28/48720.aspx)

That post is four years old....

How relevant is it?

Anyone have any hard info on it?

Firefox has gone through some big changes in that time...

---

### Post by 73ckn797 on 2009-05-26
> **egalvan said:**
> That post is four years old....

How relevant is it?

Anyone have any hard info on it?

Firefox has gone through some big changes in that time...

I find that it still works. Most of the settings are already in Firefox and you are only tweaking those. Several are additional add-ins.

Here: [http://www.tweakguides.com/Firefox_1.html](http://www.tweakguides.com/Firefox_1.html) is an updated tweaking guide that has the same tweaks from the earlier link. Different pages and authors, same tweaks generally. I think that it is relevant.

---

### Post by egalvan on 2009-05-29
> **73ckn797 said:**
> I find that it still works. Most of the settings are already in Firefox and you are only tweaking those. Several are additional add-ins.

Here: [http://www.tweakguides.com/Firefox_1.html](http://www.tweakguides.com/Firefox_1.html) is an updated tweaking guide that has the same tweaks from the earlier link. Different pages and authors, same tweaks generally. I think that it is relevant.

Thanks.
I had forgotten about TweakGuides.

---

