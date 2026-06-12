---
title: "getting dell bh200 bluetooth headset to work with ubuntu 8.10"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by djmh on 2009-04-06
well , i really dont know what to do to get my bluetooth headset to work
ive searched these forums and google , but none of the solutions i found have worked
by the way , i can get my bluetooth mouse to work
and i can get the heeadset to be recognized , just music wont play out of it . and im at a loss as far as what i should do .
thanks for your help .

---

### Post by LowSky on 2009-04-06
try these links
[http://blueman-project.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman-project.org/index.php?option=com_content&view=article&id=51&Itemid=56)
[http://bluetooth-alsa.sourceforge.net/](http://bluetooth-alsa.sourceforge.net/)

---

### Post by djmh on 2009-04-06
whew , i think i intsalled those now ...
but i still cant get it to work ..
any other suggestions ?

---

### Post by Son of Silas on 2009-05-13
Suggestion... Throw away your headset and buy a different one or switch to Windows. I have had one of these headsets for over a year and have tried just about everything. I have never found anyone who can get it working in Ubuntu.

Shame, because in windows it works really well.

---

### Post by godplayer on 2010-03-01
Hmm .. I also tried and find the same problem ... Please will someone tell how to solve this ..

---

### Post by Silas (son of Silas) on 2010-07-11
> **Son of Silas said:**
> Suggestion... Throw away your headset and buy a different one or switch to Windows. I have had one of these headsets for over a year and have tried just about everything. I have never found anyone who can get it working in Ubuntu.

Shame, because in windows it works really well.
OK, so after a year since my last post, these now work with Lucid... With some fiddling.

Install Bluetooth Manager form the Ubuntu software centre.

If you already have these headphones paired, delete the pairing.

Put the headphones into discovery mode by turning them on and holding the powerbutton until the light flashes.

From the System Menu, Choose Preferences then Bluetooth Manager

Select the Search button on the toolbar. When it finds your BH200, select it, type 0000 as the code. When that completes click the star on the toolbar to mark it as trusted.

Right click on the entry for Dell BH200 and choose setup.

Select A2DP (send audio) then click forward. When setup has completed close the Bluetooth Manager.

In your Panel bar, you should now have 2 bluetooth icons. 1 For Bluetooth Manager with a green dot and the regular Bluetooth icon that was there before you started all this.

left click the original Bluetooth icon, choose sound preference from the BH200 menu.

In the hardware tab, select the Dell BH200, then in the profile drop down list select High Fidelity Playback (A2DP)

In the Output tab select Dell BH200.... et Voila! your great sounding but really uncomfortable headphones that you hung onto for 2 years just in case Ubuntu ever supported them now work!!!

---

### Post by adroitster on 2010-09-12
Thanks a lot silas! That worked for me. I don't know why they don't ship ubuntu with the better bluetooth manager?

---

### Post by c2tarun on 2010-10-25
thanx silas
thanx a lot buddy, now i can watch movies. :)

---

### Post by hlslaughter on 2010-10-27
thanks silas, worked for me too. not sure if the "blueman" piece is necessary as headset still works when it's not running, but this is after setting it up using your steps.

sad it's so hard to get this set up :(

---

### Post by c2tarun on 2010-10-30
[LEFT]if u want to take a look how to do it.
visit: [http://tricksfind.blogspot.com/2010/10/connect-dell-bh200-headset-on-ubuntu.html](http://tricksfind.blogspot.com/2010/10/connect-dell-bh200-headset-on-ubuntu.html)
i added all the necessary screenshots there.
[/LEFT]

---

### Post by TedinOz on 2011-01-13
Thanks for a great and simplified set of instructions. It was good to see that it helped so many solve this problem but alas, I am trying to connect sound to a Motorola H350 bluetooth headset, running Ubuntu 10.1 and whilst I was hopeful of a break-through, no dice. The headset is only mono but I need to connect both input and output for use on computer sound (video and music) as well as VOIP telephony with skype.

If anyone has any suggestions along these lines in my case it will be greatly appreciated. Bluetooth connection with Blueman is fine but when I get to sound preference options they are restricted by comparison to the examples shown in the blog of c2tarun.  Also I read in another post somewhere to check whether PulseAudio is connected as a plugin within Bluetooth Manager by right clicking the new bluetooth icon, selecting plugins and checking PulseAudio. On mine it is listed as a plugin but greyed out and inactive and to check the box doesn't work. Screenshots below to show what is happening here. 

Anyone, please help if you can...very confused here, :confused:

[ATTACH]180920[/ATTACH]

[ATTACH]180921[/ATTACH]

[ATTACH]180922[/ATTACH]

[ATTACH]180923[/ATTACH]

---

### Post by TedinOz on 2011-01-13
A further screenshot is attached here to illustrate my point about connecting the plugin[ATTACH]180924[/ATTACH]

---

