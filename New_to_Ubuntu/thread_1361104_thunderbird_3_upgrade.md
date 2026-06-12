---
title: "thunderbird 3 upgrade"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by DarinB on 2009-12-21
1. is Thunderbird 3 worth the upgrade? in Jaunty
2. I have many folders and add ons ie gmail, signature switch, Lookout tnef integrator. Don't want to loose this stuff????
3. How do i upgrade it easily?
is there a ppa?

---

### Post by tom.swartz07 on 2009-12-21
> **DarinB said:**
> 1. is Thunderbird 3 worth the upgrade? in Jaunty
2. I have many folders and add ons ie gmail, signature switch, Lookout tnef integrator. Don't want to loose this stuff????
3. How do i upgrade it easily?
is there a ppa?

3.) sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
2.) shouldnt change anything, just update the version
1.) Its a little faster, and there are quite a few new features. See [http://www.mozillamessaging.com/en-US/thunderbird/3.0/releasenotes/](http://www.mozillamessaging.com/en-US/thunderbird/3.0/releasenotes/) for new changes.


NOTE: this will also update your Firefox to the newest build also. It MIGHT rename it to the 'codename' of the build "Shiretoko" is the newest one.

Hope it helps!

---

### Post by DarinB on 2009-12-21
I have a problem with that i locked my firefox and am keeping it at 3.015 it works a lot better on my system no crashes or shut downs. any way to upgrade with out affecting firefox?

---

### Post by tom.swartz07 on 2009-12-21
> **DarinB said:**
> I have a problem with that i locked my firefox and am keeping it at 3.015 it works a lot better on my system no crashes or shut downs. any way to upgrade with out affecting firefox?

Well, you have 2 options, just dis-select the firefox updates from the update manager when they show up, or

add ```
deb http://ppa.launchpad.net/fta/ubuntu karmic main
``` to your sources list.

Not to sound rude, but you WILL be nagged for firefox updates, as there are quite a few updates since your version, a few of which fix security holes.

Hope this helps

---

### Post by DarinB on 2009-12-21
will this be the same for jaunty just change the name from karmic to jaunty?

---

### Post by DarinB on 2009-12-21
any other way to install tbird 3?

---

### Post by wilee-nilee on 2009-12-21
Install the ppa update install t3 then turn off the ppa in software sources or via the apt source list.

---

### Post by DarinB on 2009-12-21
where do i find the ppa for jaunty? with the pub key

---

### Post by wilee-nilee on 2009-12-21
> **DarinB said:**
> where do i find the ppa for jaunty? with the pub key

2nd post has all the info it will install the kay as well.

---

### Post by kermiac on 2009-12-21
If you only want to update thunderbird, ubuntuzilla might be more suitable.
All the relevant info can be found at the website below.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

---

### Post by DarinB on 2009-12-21
i added shredder 3 mail, not too pleased with it how do i remove it...now that i tried it????

---

### Post by wilee-nilee on 2009-12-22
It should be in synaptic, how did you install it?

---

### Post by DarinB on 2009-12-22
can't find it in synaptic!! not under shredder 3 mail or thunderbird all i see is the old 2.0023?

---

### Post by DarinB on 2009-12-22
ok now i want to try again, i removed the shredder version and i want to upgrade what i have. when i added the shredder version it installed it and it was a seperate install i want an upgrade so i can just use the new version? what is the best way to do that?

---

