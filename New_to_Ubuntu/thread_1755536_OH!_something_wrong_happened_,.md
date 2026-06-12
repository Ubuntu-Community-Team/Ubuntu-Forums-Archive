---
title: "OH! something wrong happened ,"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-05-11
hey everyone....
   i upgraded to ubuntu 11.04 and then found unity was not my kind of thing especially when there were no visual efects even after ati graphics card 1 gb,, so i installed gnome3.  there  seemed to be some conflict between unity and gnome3 and though at login screen i chose gnome shell i use to get a distorted unity. then i found a way out,, i use to run on terminal 
[code] compiz --replace ]/code]
and i use to stop it in middle using ctrl +c , i would then get gnome 3 . though a distorted one.. yesterday i updated my system and now when i login using any of gnome shell ,ubuntu , unity 2d or netbook edition i get the error ""oh! something wrong happened , please log out and try again"" whats the problem with my system and how can i solve . please help

---

### Post by Frogs Hair on 2011-05-11
Gnome 3 will break Unity and from what I have read the upgrade can't be reversed . Unity runs on Gnome 2.xx and you now have Gnome 3.

Most of the instructions I have seen for upgrading to Gnome 3 are very clear about the fact that it will break unity . I think you have either try and get Gnome 3 working or backup your data if possible and reinstall.

---

### Post by vivek.pandey on 2011-05-11
> **Frogs Hair said:**
> Gnome 3 will break Unity and from what I have read the upgrade can't be reversed . Unity runs on Gnome 2.xx and you now have Gnome 3.

Most of the instructions I have seen for upgrading to Gnome 3 are very clear about the fact that it will break unity . I think you have either try and get Gnome 3 working or backup your data if possible and reinstall.

can you please suggest some way to get gnome 3 back.. i cant login in any of them

---

### Post by Muskegman on 2011-05-11
Same thing happened to me a month ago when I was testing Beta1 11.04, installed Gnome3 and Unity was gone.
Unfortunatley the only thing I could do was a full reinstall and start again.

---

### Post by vivek.pandey on 2011-05-11
> **Muskegman said:**
> Same thing happened to me a month ago when I was testing Beta1 11.04, installed Gnome3 and Unity was gone.
Unfortunatley the only thing I could do was a full reinstall and start again.

sorry to say but reinstalling is the last option i keep for myself.... reinstalling again and again is i feel an option which not allows a person to learn anything about computers or os... i have faced many problems whether it be ubuntu or earlier windows but never reinstalled anything... i will try to save my ubuntu installation first ;-)

---

### Post by vivek.pandey on 2011-05-12
hey anyone please?

---

### Post by old_codger on 2011-05-12
> **vivek.pandey said:**
> hey anyone please?
When you say unity 'wasn't your thing', do you mean it hasn't got enough effects or do you just mean it didn't work properly? If it's just a matter of graphics corruption couldn't you simply select 'Classic Ubuntu' or 'Classic Ubuntu - no effects' at the bottom of the login screen?

That's what I ended up doing with my old NVidia card which seemed to have problems.

---

### Post by vivek.pandey on 2011-05-12
> **old_codger said:**
> When you say unity 'wasn't your thing', do you mean it hasn't got enough effects or do you just mean it didn't work properly? If it's just a matter of graphics corruption couldn't you simply select 'Classic Ubuntu' or 'Classic Ubuntu - no effects' at the bottom of the login screen?

That's what I ended up doing with my old NVidia card which seemed to have problems.

yeah you are right . it didnt have effects like desktop cube and all those animaton effects.... and about classic ubuntu... i initially did have the option and i use to work on it but after installing gnome3 , its gone . its not there. i have a unity 2d option though but i get the above mentioned error when i choose it...:-(

---

### Post by arsenic23 on 2011-05-12
You could try to apt-get purge gnome3 and unity (or ubuntu-desktop), and then reinstall them.  If you are not comfortable with that you might just be digging a deeper hole though.

---

### Post by vivek.pandey on 2011-05-12
> **arsenic23 said:**
> You could try to apt-get purge gnome3 and unity (or ubuntu-desktop), and then reinstall them.  If you are not comfortable with that you might just be digging a deeper hole though.

thanx for your reply but
perhaps you didnt read my first post... when i login i get an error so how can i purge gnome3 or anything?

---

### Post by arsenic23 on 2011-05-12
> **vivek.pandey said:**
> thanx for your reply but
perhaps you didnt read my first post... when i login i get an error so how can i purge gnome3 or anything?

Oh.  Sorry.  Just hit ctrl+alt+F1 (or any of the F keys really) and log in with the console.  You can ctrl+alt+F7 to get back to the GUI.

---

### Post by vivek.pandey on 2011-05-12
> **arsenic23 said:**
> Oh.  Sorry.  Just hit ctrl+alt+F1 (or any of the F keys really) and log in with the console.  You can ctrl+alt+F7 to get back to the GUI.

that cant be done either as that error message obviously prevents anything to be pressed before cancelling it but there is no option  to cancel it.. only one option to logout..

---

### Post by compmodder26 on 2011-05-12
You can boot into recovery mode and launch a root command prompt with networking.

Reboot your computer and immediately after your BIOS screen goes away, hold shift until the grub menu appears.  Then select recovery mode and a menu will eventually appear where you can select the root command prompt with networking.  Then you can try the suggestion by arsenic23.

---

### Post by arsenic23 on 2011-05-12
> **vivek.pandey said:**
> that cant be done either as that error message obviously prevents anything to be pressed before cancelling it but there is no option  to cancel it.. only one option to logout..

Do it before you log in.

---

### Post by astex on 2011-05-12
If you are given a login screen or an error screen, type ctrl+alt+F1 at that screen (ctrl+option+F1 on macs).  This will give you a virtual login terminal through which you can login using no display manager.  From there it is very easy to remove everything gnome3 related.  Simply run:

  $ sudo ppa-purge ppa:gnome3-team/gnome3

then:

  $ sudo apt-get update
  $ sudo apt-get upgrade
  $ reboot now

should bring you back to the default installation (assuming you have not installed anything that depends on gnome3 or gnome-shell).  Also, does booting into LXCE give you an error as well?  By default, this installs along-side gnome3.

---

### Post by vivek.pandey on 2011-05-12
ok i messed everything up.... i purged gnome3 using
```

sudo apt-get purge gnome-shell
sudo apt-get autoremove gnome-shell

```
and then rebooted i got into ubuntu but it looks really ugly a blue login screen . i didnt have the option of gnome shell . thats alright .. i was hesitating to use this purge method because i use mobile broadband and not wired internet and dont have wvdial installed so i could not connect to internet as when i logged in it was just a blue screen nothing else . ctrl + alt+t got me a terminal that too very ugly . but i cant close anyhting i open...

---

### Post by Durden on 2011-05-12
Just reinstall. Will take 15 minutes. You could have reinstalled 20 times by now with all the effort you've put in on this.

Spare yourself the pain and just reinstall the OS

---

### Post by astex on 2011-05-12
You removed the old window manager but did not reinstall gnome2 or unity.  If you want gnome3 back, press ctrl+alt+F1 run:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

Otherwise, remove the gnome3 repository using ppa-purge as described above, then update and upgrade.  Do not reboot without a window manager.  It will boot using the default xinitrc (into twm).

---

### Post by vivek.pandey on 2011-05-12
> **Durden said:**
> Just reinstall. Will take 15 minutes. You could have reinstalled 20 times by now with all the effort you've put in on this.

Spare yourself the pain and just reinstall the OS

sorry reinstalling it is out of question.... there has to be some way out..i student who recently hacked his college website and then helped them to build a better one ... its not impossible,.... the only thing i will not do is reinstalling.. i will search for some way out using my broadband connection else will go tomorrow to college internet lab and fix things ... i am sorry if you think me a kinda attitude headed guy but its not just an os for me.. its a place were i spend almost 14 hours a day or even more.... i had made it a real eye candy with al those beautiful stuffs like macbuntu , cube , water effects , cairo dock... when i didnt get all these in ubuntu 11.04 i was kinda sad but i will make it work somehow.... and besides i have windows 7(though i seldom use it) , archlinux and one more ubuntu 10.10 installed in my laptop plus fedora ,xp and backtrack installed in virtualbox so i am not in dearth of os ;-)

---

