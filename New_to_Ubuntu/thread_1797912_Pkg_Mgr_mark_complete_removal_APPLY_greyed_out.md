---
title: "Pkg Mgr mark complete removal APPLY greyed out"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by jfbooth on 2011-07-05
I uninstalled 2 packages  gnome-sudoku  and  brltty-x11.

Using Package Manager, it shows these as 'Not Installed (residual config)'.

There is a tutorial on cleaning up 'junk' which says to use this and mark these for 'complete removal' which I have done .. but to apply the routine, the 'apply' button is grayed out.

Any help is appreciated in advance.

Xubuntu 11.04

---

### Post by jtarin on 2011-07-05
I assume this is Synaptic Package Manager your referring too? Do you have a link to the tutorial?

---

### Post by jfbooth on 2011-07-05
> **jtarin said:**
> I assume this is Synaptic Package Manager your referring too? Do you have a link to the tutorial?

Yes, Synaptic Package Manager.

Here is a link to the tutorial:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

"Tip #1 - Getting rid of Residual Config packages - In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to System > Administration > Synaptic Package Manager. On the bottom left hand corner of the window, click the Status button. In the list above the Sections, Status, Search, and Custom buttons, you should see the following text:


> Installed
Installed (local or obsolete)
Not installed
Residual config  

Click on the "Residual config" text. (If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine and you can skip down to Tip #2.)

Do you see the packages that popped up in the window on the right? Those are the Residual Config packages. To get rid of these pests, click on the box to the left of the package name and select "Mark for Complete Removal". After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window. Do you see the green check mark with the text "**Apply**" right under it? Click that button, and you'll flush all those Residual Config packages down the toilet!"

---

### Post by jtarin on 2011-07-05
I use [UbuntuTweak]("http://ubuntu-tweak.com/") for this.....much easier....be cautious though.
Most of your configs can be found in your home folder....usually they are hidden.

---

### Post by jfbooth on 2011-07-05
> **jtarin said:**
> I use [UbuntuTweak]("http://ubuntu-tweak.com/") for this.....much easier....be cautious though.
Most of your configs can be found in your home folder....usually they are hidden.

Uhmm OK.  I will take a look at 'Tweak .. but I would still feel good about why SPM has 'apply' greyed out.  Thank you very much for the 'Tweak tip and link.

---

### Post by cmcanulty on 2011-07-05
just a guess but maybe the complete removal would remove something needed for system or another app.

---

### Post by Rex Bouwense on 2011-07-05
+1 for Tweek.  I have used Ubuntu Tweek also but I also use BleachBit which is also great.

---

### Post by jtarin on 2011-07-05
> **jfbooth said:**
> Uhmm OK.  I will take a look at 'Tweak .. but I would still feel good about why SPM has 'apply' greyed out.  Thank you very much for the 'Tweak tip and link.Normally when you uninstall something with Synaptic you would right-click on the application in the list and choose complete removal.....not all applications offer complete removal for one reason or another.You can always research what files an application installs if you don't think it has removed all you want.Be cautious.

---

### Post by jfbooth on 2011-07-05
> **jtarin said:**
> Normally when you uninstall something with Synaptic you would right-click on the application in the list and choose complete removal.....not all applications offer complete removal for one reason or another.You can always research what files an application installs if you don't think it has removed all you want.Be cautious.

I have followed the tutorial several times and this is the first time it found "residual"s where the apply button was greyed out.  Not worried too much about it .. mostly curious.  I'm going to look at 'TWEAK and see what it offers.  I will 'be careful'.

Meantime, maybe someone else can 'splain this.  Thank you all for the kind replies.

---

### Post by jtarin on 2011-07-05
> **jfbooth said:**
> I have followed the tutorial several times and this is the first time it found "residual"s where the apply button was greyed out.  Not worried too much about it .. mostly curious.  I'm going to look at 'TWEAK and see what it offers.  I will 'be careful'.

Meantime, maybe someone else can 'splain this.  Thank you all for the kind replies.
[Explanations Galore!!!]("https://encrypted.google.com/#hl=en&sugexp=bvie&xhr=t&q=synaptic+residual+where+the+apply+button+was+greyed+ou&cp=17&gs_gbg=56Fe3&qe=c3luYXB0aWMgcmVzaWR1YWwgd2hlcmUgdGhlIGFwcGx5IGJ1dHRvbiB3YXMgZ3JleWVkIG91&qesig=ZNE35CiVSC3NLBnSR9icVw&pkc=AFgZ2tltokoMtkn65jSCtn6duKz1P5c_NzjMrBiWPlfJ5l8TBrBF7l6ZfMuD-PWBjNZY2yjfzSQvIzfrmKk87cI61USzEZoGfQ&pf=p&sclient=psy&source=hp&aq=f&aqi=&aql=&oq=synaptic+residual+where+the+apply+button+was+greyed+ou&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=64dbd374eaa39b9c&biw=1366&bih=639&bs=1")
An update might come along to fix that on your install.
If I can't come in the front door, I'll use the back.

---

### Post by wildmanne39 on 2011-07-05
Hi, if you want to get rid of the files and you know the names of the files you can use this command.
```
sudo apt-get --purge remove packagename
```
please make sure removing the files will not damage your system first.

---

