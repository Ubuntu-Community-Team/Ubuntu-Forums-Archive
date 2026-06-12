---
title: "compiz"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Whitsboy on 2010-11-13
Hi All,

I have just received a message from update manager that there was some updates, which i proceeded to install. Now i find that the extra plugins for compiz has been uninstalled. I have tried to reinstall it but i receive a message "compiz-fusion-plugins-extra:
 Depends: compiz-core-abiversion-20091102". Can this be fixed?
Thanks

---

### Post by coffeecat on 2010-11-13
Which version of Ubuntu are you using? That sounds like a Natty Narwhal issue.

A routine upgrade should not remove compiz-fusion-plugins-extra in Lucid or Maverick. But compiz-fusion-plugins-extra was auto-removed in a recent update in  Natty. Such package incompatibilities are to be expected at such an early stage of pre-alpha testing.

If you are testing the pre-release of Natty, you need to follow the Natty subforum.

---

### Post by ikt on 2010-11-13
> **coffeecat said:**
> Which version of Ubuntu are you using? That sounds like a Natty Narwhal issue.

A routine upgrade should not remove compiz-fusion-plugins-extra in Lucid or Maverick. But compiz-fusion-plugins-extra was auto-removed in a recent update in  Natty. Such package incompatibilities are to be expected at such an early stage of pre-alpha testing.

If you are testing the pre-release of Natty, you need to follow the Natty subforum.

I think it looks like he might be using a PPA or used a script to install something compiz related, it has now updated and broken itself.

If you go into synaptic, and check under settings > repositories, and untick any PPA's you don't recognise.

Then do,

sudo apt-get purge compiz

then restart and do,

sudo apt-get install compiz

It might fix it :s

---

### Post by coffeecat on 2010-11-13
> **ikt said:**
> I think it looks like he might be using a PPA or used a script to install something compiz related, it has now updated and broken itself.

Indeed, I wondered if the OP might be using non-standard repositories in Lucid or Maverick.

---

### Post by ikt on 2010-11-13
> **coffeecat said:**
> Indeed, I wondered if the OP might be using non-standard repositories in Lucid or Maverick.

I'm only guessing based on similar search results for 

""compiz-fusion-plugins-extra: Depends: compiz-core-abiversion-20091102""

Their post history doesn't lend me to believe their testing natty.

---

### Post by Whitsboy on 2010-11-13
No I'm not testing natty, I have only installed maverick last week.

---

### Post by Whitsboy on 2010-11-13
I have just purged compiz, done a restart & reinstalled compiz & I still get the same message. Sorry I'm new to ubuntu & I don't know too much about it.

---

### Post by coffeecat on 2010-11-13
> **Whitsboy said:**
> No I'm not testing natty, I have only installed maverick last week.

... and do you have any PPA or other 3rd-party repositories enabled? Because neither of my Mavericks wants to take out  compiz-fusion-plugins-extra.

---

### Post by Whitsboy on 2010-11-13
> **coffeecat said:**
> ... and do you have any PPA or other 3rd-party repositories enabled? Because neither of my Mavericks wants to take out  compiz-fusion-plugins-extra.
All unknown PPAs & repositories were disabled. I have gone through the purge process again & I still get the same message.

---

### Post by coffeecat on 2010-11-13
This is very curious. In Synaptic (in Maverick), dependencies listed for compiz-fusion-plugins-extra include compiz-core, and my installed version is 1:0.8.6-0ubuntu9.1, and also compiz-core-abiversion-20091102. But compiz-core-abiversion is not listed in Synaptic, nor can I find a package for it in my apt cache.

However, I found this:

[http://packages.ubuntu.com/maverick/compiz-core-abiversion-20091102](http://packages.ubuntu.com/maverick/compiz-core-abiversion-20091102)

Try (re)installing compiz-core (which should have been pulled in with your reinstallation of compiz) and see if that makes any difference. If not post back and we'll do some more digging. This might be related to the compiz shenanigans we've experienced recently in Natty after all.

---

### Post by Whitsboy on 2010-11-13
> **coffeecat said:**
> This is very curious. In Synaptic (in Maverick), dependencies listed for compiz-fusion-plugins-extra include compiz-core, and my installed version is 1:0.8.6-0ubuntu9.1, and also compiz-core-abiversion-20091102. But compiz-core-abiversion is not listed in Synaptic, nor can I find a package for it in my apt cache.

However, I found this:

[http://packages.ubuntu.com/maverick/compiz-core-abiversion-20091102](http://packages.ubuntu.com/maverick/compiz-core-abiversion-20091102)

Try (re)installing compiz-core (which should have been pulled in with your reinstallation of compiz) and see if that makes any difference. If not post back and we'll do some more digging. This might be related to the compiz shenanigans we've experienced recently in Natty after all.
Reinstalled compiz-core & am getting same result.

---

### Post by coffeecat on 2010-11-13
> **Whitsboy said:**
> Reinstalled compiz-core & am getting same result.

It gets even curiouser. I marked compiz-fusion-plugins-extra for reinstallation and it had to download the package even though this is a system I set up only a week ago in which I had already installed the plugins-extra package and I haven't done an 'apt-get clean' since.

Be that as it may, it downloaded and installed it without any error.

I am almost out of ideas, except: do you have a 32-bit or 64-bit system? Mine is 64-bit, but if you are running 32-bit there might just possibly be a bug that you've uncovered.

---

### Post by Whitsboy on 2010-11-13
> **Whitsboy said:**
> Reinstalled compiz-core & am getting same result.
I have version 1:0.9.0-0ubuntu1~ppb1 installed. I have no compiz-core-abiversion-20091102

---

### Post by Whitsboy on 2010-11-13
> **coffeecat said:**
> It gets even curiouser. I marked compiz-fusion-plugins-extra for reinstallation and it had to download the package even though this is a system I set up only a week ago in which I had already installed the plugins-extra package and I haven't done an 'apt-get clean' since.

Be that as it may, it downloaded and installed it without any error.

I am almost out of ideas, except: do you have a 32-bit or 64-bit system? Mine is 64-bit, but if you are running 32-bit there might just possibly be a bug that you've uncovered.
I have a 32-bit.

---

### Post by coffeecat on 2010-11-13
> **Whitsboy said:**
> I have a 32-bit.

I have no 32-bit system to check this. Maybe this is an issue with 32-bit only. Perhaps someone running a 32-bit system may be able to comment. I'll do a search but I may not be able to get back to this thread for a few hours.

---

### Post by wkhasintha on 2010-11-13
Which version of Ubuntu are you using? That sounds like a Natty Narwhal issue.

A routine upgrade should not remove compiz-fusion-plugins-extra in Lucid or Maverick. But compiz-fusion-plugins-extra was auto-removed in a recent update in Natty. Such package incompatibilities are to be expected at such an early stage of pre-alpha testing.

If you are testing the pre-release of Natty, you need to follow the Natty subforum.

---

### Post by coffeecat on 2010-11-13
> **coffeecat said:**
> Which version of Ubuntu are you using? That sounds like a Natty Narwhal issue.

A routine upgrade should not remove compiz-fusion-plugins-extra in Lucid or Maverick. But compiz-fusion-plugins-extra was auto-removed in a recent update in  Natty. Such package incompatibilities are to be expected at such an early stage of pre-alpha testing.

If you are testing the pre-release of Natty, you need to follow the Natty subforum.

> **wkhasintha said:**
> Which version of Ubuntu are you using? That sounds like a Natty Narwhal issue.

A routine upgrade should not remove compiz-fusion-plugins-extra in Lucid or Maverick. But compiz-fusion-plugins-extra was auto-removed in a recent update in Natty. Such package incompatibilities are to be expected at such an early stage of pre-alpha testing.

If you are testing the pre-release of Natty, you need to follow the Natty subforum.

Is it just my ears, or is there an echo in here? :-k

---

### Post by luke123 on 2010-11-13
I am also having this issue and have been looking for help.
I am using 32-bit Maverick. I recently, yesterday, did a partial-upgrade which included removing compizfusion-plugins-extra, I thought this was odd but there was no option not to so I let it. I did have a ppa for compiz ([http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu)) but I disabled this and then reinstalled compiz, and I still have this problem. Running compiz --version tells me it is Compiz 0.9.0.
When I try to install compizfusion-plugins-extra I also get ```
The following packages have unmet dependencies.
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packages
```
When I run compiz --replace --debug all of the windows flash and I get this output:
```
$ compiz --replace --debug
compiz (core) - Debug: Could not stat() file /home/luke/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/luke/.compiz-1/plugins/libmove.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/luke/.compiz-1/plugins/libresize.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/luke/.compiz-1/plugins/libplace.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/luke/.compiz-1/plugins/libdecor.so : No such file or directory

```
Also, it does not fall back to metacity, instead it just looks broken, there are no title bars and my two docks do not hide but are permanently there and my browser window is enclosed by them. Not a very good explanation I know so I have attached a screenshot. It goes back to normal when I run metacity --replace.
Any help on this would be appreciated, I miss my compiz.

---

### Post by digital-daniel on 2010-11-17
I have a similar problem. This morning I had a partial upgrade and then after I rebooted I didn't have any windows decorations, and compiz if broken.

I get the message:

Can't load plug-in decorations
I have have the same dependency issues as you have described above. 

Confused 


Daniel
Definitely Maverick, I've not changed any PPAs recently

---

### Post by javaholic on 2010-11-17
I think there seems to be alot of confusion over what has happened but it looks to be explained quite well here:

[http://www.omgubuntu.co.uk/2010/11/compiz-adds-natty-ppa/](http://www.omgubuntu.co.uk/2010/11/compiz-adds-natty-ppa/)

quoting directly from that page here:

"I intially reported that this was a PPA for Natty which was incorrect. To plagiarise Sam’s words,  here is how I arrived at the conclusion that this was/is/should/could/maybe be a PPA for Natty: -

    "Didier, Travis and I got the various bits and pieces together for an Ubuntu Natty PPA for Compiz 0.9.x!"

The PPA is, in fact, for Maverick users  – as the very ace didrocks pointed out in the comments below – as the PPA doesn’t contain a single Natty package."

Hopes this sort of some of the confusion.

the newer compiz looks really nice and neat i might continue using this PPA and wait for it to kick into life for the time being.

---

### Post by digital-daniel on 2010-11-17
Thanks for that, 

I'm still uncertain what I need to do to get it working again. Could I trouble you for a little more help please.

Many thanks

daniel

---

### Post by javaholic on 2010-11-19
digital-dan, are you looking for a PPA where the updated compiz works cause to get my compiz 0.9.2 i followed the instructions found here:

[http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html](http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html)

To get Compiz to start on system start you'll have to add that compiz --replace line to the startup applications found inside preferences.

If you want to revert to the previous compiz version then this should work for you:

[http://ubuntuforums.org/showpost.php?p=9964610&postcount=2%20_](http://ubuntuforums.org/showpost.php?p=9964610&postcount=2%20_)

not tried it myself but i think that should work for you.

---

### Post by digital-daniel on 2010-11-19
Thank you so much for your help.

It worked a treat.

Daniel

---

### Post by wkhasintha on 2010-11-21
> **coffeecat said:**
> Is it just my ears, or is there an echo in here? :-k

May be it is your ears . better have them checked (jk):D

---

