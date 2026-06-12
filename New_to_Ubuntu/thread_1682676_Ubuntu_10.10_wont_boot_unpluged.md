---
title: "Ubuntu 10.10 wont boot unpluged"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Ger5 on 2011-02-06
Im very new to this.However i have got rid of  windows 7 of my laptop and installed ubuntu 10.10 So for the past week  or so have done a lot o testing and stuff.laptop i have is hp pavilion  tx 2000 model tx 2130ea.
Problem i have is laptop wont boot when unplugged but boots when plugged  in.When it  starts up you can hear the logo music but screen remains  black.
Now i have found what the problem is after hours of fault finding.But dont know how to fix
Ubuntu detects the additional drivers to download wireless driver etc  and a couple of nvidia 2d/3d drivers so its when one these nvidia drivers  are in stalled is what causes the problem when booting up unplugged.No  problem when plugged in.At the moment i just have not installed these  nividia drivers and all is good just wondering is there a fix for this.
 Graphics Card Nvidia Geforce Go 6150

---

### Post by ajgreeny on 2011-02-06
So install those drivers straight away!  Why the delay?

I am not sure why it should matter if you are on mains electricity or battery power, so would be interested to hear more of your problem.  When you say plugged in, do you mean mains power, or connected to the internet?

---

### Post by Ger5 on 2011-02-06
when its not plugged into mains power it wont boot .sorry it boots i can see the hp logo . However when it kicks into ubuntu its just a black screen i think it loads up to the logon screen because it plays the logon music. not that it matters to much the odd time i might use lap top on battery power. excellent effects when drivers are installed just though there might be a fix or that i done something wrong

---

### Post by ajgreeny on 2011-02-06
So just go ahead and properly install the driver you need.  Are you sure this is not just a live CD you are using?

---

### Post by Ger5 on 2011-02-06
no its not a live cd i have fully in stalled ubuntu 10.10 as the main os nothing else on the laptop

---

### Post by jroa on 2011-02-06
If you boot up while plugged in, then unplug the cord, what happens?  If the screen goes blank, then what happens when you plug back in?

This is very strange and it could be a power saving setting that is not work right.  I do not use Ubuntu on a laptop, but I have one with Fedora on it.  I have it set so that screen brightness dims after a few seconds of no activity when using battery, but it comes right back when you touch any key.  Maybe this is not working right on your installation?

---

### Post by Ger5 on 2011-02-07
yes it is a strange one.when unplugged it boots shows the ubuntu screen little dots changing colour loading fine, just when its about to switch to the logon screen the screen goes blank.However i can hear the logon music and even dough its a blank screen i type my user name and password and the screen still stays blank but i can hear it loading up to the desktop screen.

Now when i boot plugged in no problem at all . when its fully booted up removing the power cord has no effect stiil ok and even when it goes into hibernation and i log back on no problem. i have tryed a lot of basic stuff. i do have all power setting  ie dim etc to a minimum.i also have tryed  reinstalled ubuntu no joy also i tryed updating and  even not updating just loading the basic os still no joy . .this only accrues when i install the nvidia driver. if i dont install the driver it boots fine both unplugged and plugged i have also tryed other os ie linux mint and the same problem happens.

i reinstalled the nvidia driver today and still the same ie when unplugged it boots shows the ubuntu screen  little dots changing colour loading fine, just when its about to switch  to the logon screen the screen goes blank.However i can hear the logon  music in tne back ground now at this stage if i hold down the (fn) function button along with the f5 botton( which its second function is to put the laptop into hibernate) and when both buttons  are released about one second later the laptop goes into sleep mode fine and then i hit any key to bring it out of sleep mode ok. now the interesting bit.when it comes out of sleep mode i can see the logon screen type in password and every thing works fine .a rather long way round to boot laptop unplugged from mains strange.

---

