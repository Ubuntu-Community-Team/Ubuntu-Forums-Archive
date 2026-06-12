---
title: "Why am I having NO LUCK with Jaunty on any of my computers!"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by ready4thebreak on 2009-06-02
I have two major problems with Jaunty on each of my laptops. I can't activate desktop effects on my Gateway ML6732(when I had full compiz fusion running with 3D acceleration on Hardy) and my HP mini 1030nr netbook will not play sound out of the speakers(when again it did on Hardy). My Gateway has an Intel GM965 with the Intel Graphics Media Accelerator X3100. And my HP was the typical netbook chipset with the Atom N270.

I've constantly been looking online for help with either conflicting help or people saying that it didn't work. I figured I would make my own post to get this done once and for all. 


I know most are going to recommend going back to an older distro, but I really like Jaunty's stability, optimization of processes, and better battery life.

I've always gotten great help on these forums, so ANY help is more than welcomed.

---

### Post by goldblattster on 2009-06-02
Do you have intel integrated stuffs?

---

### Post by ready4thebreak on 2009-06-02
yeah they're both laptops so it's all Intel intergrated stuff.

---

### Post by TheNosh on 2009-06-02
the 3D drivers got blacklisted. 

i enabled them anyway through the command on this page:
[INDENT][http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)[/INDENT]

works fine for me, your mileage may vary


as for sound issues, i got nothin'
good luck though

---

### Post by ready4thebreak on 2009-06-03
Graphics work great now! Thanks for the help. Why exactly are the graphics blacklisted? Is it one of those things that may become a problem later on? But that code worked flawlessly. If it was so easy to reverse, why would they even bother?

---

### Post by TheNosh on 2009-06-03
it **can** cause your system to hang. as i said i haven't had much trouble with it. however as a precautionary measure i turn off compiz when doing anything important, and i advise you to do the same just in case

---

### Post by theozzlives on 2009-06-03
Jaunty is having problems with Intel graphics. I bypassed my laptop and it worked fine, not true with my desktop. I had to buy an NVidia card.

---

### Post by prvteprts on 2009-06-03
Regarding the sound problem...

Don't despair. The sound on Intrepid on my laptop worked out of the box, but when I upgraded to Jaunty, I just had to add some lines to /etc/modprobe.d/alsa-base.conf which I think are based on the model of my sound card. Anyway the lines I added were: 

options snd-hda-intel model=hp-m4
options snd-hda-intel enable_msi=1

However, my laptop is a HP Compaq Presario. If these don't work, try looking for the lines for your specific laptop model.

---

### Post by ready4thebreak on 2009-06-03
Thank you all so much. 

What exact problems is Jaunty having with Intel graphics if all these people are just adding these lines and not having any issues? (This is sheerly a question of curiousity)

And to Prvteprts how would I find out those lines? (I'm google searching them with little luck)

Is this going to be a normal thing with each distro? Because when I got Hardy everything went flawlessly(even though the an old trial desktop I have installed Jaunty flawlessly, PCI cards and all). I never thought upgrading would be a headache(it hasn't been a big issue for me thus far but I'm seeing massive amounts of people really getting pissed over these similiar issues). Because if it is I guess I'll just be sticking to only LTS installs even though they aren't always the latest and greatest. I only install Ubuntu on my laptops usually and things like battery life and Wifi support are big deals. They were somewhat difficult to get answers and solutions for on Hardy but worked perfect on Jaunty. It's like a big game of wins and losses. I love Linux the most truly. I'm considering going to school to become a Red Hat Enterprise maintainer or doing something to help Linux, but these distros will be massive headache when every 6 months they leave unresolved issues that most users couldn't even begin to understand.

Maybe I should just find one distro and stick with it, but I think I deserve kernel updates and all that, just as much as someone who updates with each distro.

---

### Post by prvteprts on 2009-06-03
> **ready4thebreak said:**
> 
And to Prvteprts how would I find out those lines? (I'm google searching them with little luck)


I wish I took note of where I found those lines. I recalled having trouble googling this particular fix as well, and from what I recall there wasn't any master list for the lines you have to add.

Try including in your search the specific name of your laptop model, and also add the keywords "jaunty" and "sound". Try zooming in on the linux forum or maybe launchpad.

---

### Post by mc4100 on 2009-06-03
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904) 
> Display freezes with Intel graphics cards

Users of various Intel video chipsets reported freezes under various conditions (e. g. a few minutes after suspend on the i945, see [339091]("https://bugs.launchpad.net/bugs/339091")). In many cases, switching off desktop effects in System &#8594; Preferences &#8594; Appearance was reported to help.

If it still happens without desktop effects, you can add Option "DRI" "off" to the Device section of /etc/X11/xorg.conf, as described above. This will disable 3D acceleration and desktop effects, but makes suspend work reliably again and also avoid many types of crashes.

These freezes happen particularly often on the i965 chips ([359392]("https://bugs.launchpad.net/bugs/359392")). For that reason, desktop effects were disabled by default on this chipset in the final release. They will be re-enabled in a 9.04 Update once the problem has been fixed. 

---

### Post by ready4thebreak on 2009-06-03
> **prvteprts said:**
> I wish I took note of where I found those lines. I recalled having trouble googling this particular fix as well, and from what I recall there wasn't any master list for the lines you have to add.

Try including in your search the specific name of your laptop model, and also add the keywords "jaunty" and "sound". Try zooming in on the linux forum or maybe launchpad.

Yeah I turned to Launchpad immediately once I started having the issue, but that's the main place where NONE of the bugs have been officially solved and the directions people are posting are conflicting one another. Just look at this posting to see what I'm saying. There must be 15 different resolutions to the same issue, with each posting saying this absolutely works and then another posting saying it didn't work so they did "____." It's just a bit of a mess right now.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942)

---

### Post by ready4thebreak on 2009-06-03
> **mc4100 said:**
> [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Thanks so much for this info. That makes perfect sense. Luckily, I had no problems with it thus far. EVERYTHING works perfectly in Compiz. I let the computer suspend and come back. I shut the screen and reopened, everything worked. Rebooted and activated a bunch of stuff and it still works. That's really strange that people are having such conflicting results with this release. But none the less thanks for the info.

---

### Post by ready4thebreak on 2009-06-03
Ok. I'll leave you guys all alone now. As of right now, ALL is well. Compiz is back up. My sounding is working on my netbook once again(although it does sound a bit quieter than before, but maybe I'm losing my mind). Thank you SO SO MUCH to everyone who posted. I gotta start getting better at this so I can start to help others.

I ran the code 

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```
to enable the desktop effects(and they fully work)

I also used these instructions to get my HP Mini's speakers to work.

Step 1: Open Terminal from "Applications->Accessories->
Terminal"

Step 2: Run the following commands (copy/paste each command into the Terminal and then hit <enter>)

```
wget http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.19.2_all.deb

sudo dpkg -i alsa-driver-linuxant_1.0.19.2_all.deb

sudo gedit /etc/modprobe.d/alsa-base.conf
```

# Add following line at the end of the alsa-base.conf file and then save the change(it may be blank, but still insert these lines):

options snd-hda-intel model=laptop

# Enter following command:

```
sudo gedit /etc/modprobe.d/options
```

# Add following line at the end of the options file and then save the change(it may be blank, but still insert these lines):

options snd-hda-intel model=laptop

Step 3:
Reboot pc

Step 4: IF your volume control has disappeared from your taskbar, open Terminal from "Applications->Accessories->
Terminal" and then enter following command:

```
gnome-volume-control
```

and make sure nothing is muted.

Hope this makes everything clear and helps out everyone else.

---

### Post by TheNosh on 2009-06-03
congrats, glad to hear everything is working

---

