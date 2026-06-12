---
title: "Laptop (inspiron 1564) overheating and crashes"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by pakkatechie on 2011-02-21
Laptop (inspiron 1564) overheating and crashes with maverick 10.10. It happens mostly when browsing with flash ad and when watching flash videos just for few minutes. 
Following things i tried after searching forum and google
1. Installed sensors (hddtemp and coretemp)
2. Flash is of propriety driver with latest version
3. When i tried to add i8k, my laptop hangs. It looks like its not for my model
4. Also the FAN0 and FAN1 are always shows off state for the command 
> 
sudo cat /proc/acpi/fan/FAN*/state
status:                  off
status:                  off

5. ATI Radeon 512 mb is also with properity driver
6. One more thing I noticed is that unchanging and constant thermal_zone temp. 
> 
cat /proc/acpi/thermal_zone/TZ0*/* 
0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             27 C
critical (S5):           100 C
passive (forced):<not set>
active[0]:               71 C: devices=FAN1 
active[1]:               55 C: devices=FAN0 
0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             0 C
critical (S5):           100 C
passive:                 95 C: tc1=0 tc2=2 tsp=10 devices=CPU0 CPU1 CPU2 CPU3 CPU4 CPU5 CPU6 CPU7 
active[0]:               71 C: devices=FAN1 
active[1]:               55 C: devices=FAN0 

Please some one help me with crashing problem.  I am scared it could spoil my motherboard because of overheating. I need to watch flash videos , because of this problem i need to switch to win 7 (i never got such issues in win 7). Is it because the thermal zone  temp is constant, fan is not running and laptop crashes ? Why this crashing not happening in win 7 ? I am totally confused

---

### Post by pakkatechie on 2011-02-22
bump :-(

---

### Post by Torisuna on 2011-02-22
after a quick search on your system it seems that line of Dell Computers  (inspiron) have been know to have overheating issues because of a  design flaw. The reason I could see that windows 7 does not have an  issue (in a short amount of time) is because of the the large virtual memory windows uses on the  Hard Drive it's self. I have nuked many of windows computers in my day  because i disabled that function on windows. It sounds to me your having  a cooling issue ( as to everyone else) and I have had problems myself  using a dual core processor to gaming on a laptop for a extended period of time with windows and custom settings. Do you have a external cooling system for you laptop? They are good to have in general because laptops are really not designed to be use for very extended amounts of time. Sorry i'm not much help but i hope this can help you find some answers toward your problem now and in the future.

---

### Post by pakkatechie on 2011-02-22
Thanks for replying. 
Unfortunately I don't have external cooling system. My only concern why win 7 alone works without crashing. Linux does have swap memory silmiliar to VM in windows. But only Ubuntu crashes. Not sure why?
:-(
Any customization to avoid this crashing in ubuntu will help me a lot

Also why ACPI always shows fan OFF even when it is on? Am i missing any kernal module for my model? thermal zone temp is always 0 and 27 ? :-(

---

### Post by Sylos on 2011-02-22
Have you tried tweaking the settings in the bios regarding the fan cut in/safety cut out features?

When it crashes does it hang or does it shut itself down?

Can you actually hear the fan running when the machine gets hot?(i assume if it gets that hot the bottom of the case will be pretty toasty too). I ask this as somethimes lmsensor can not register things properly if some kernel modules arent present.

Flash is very intensive for CPUs on linux due to a lack of hardware decoding ability in flash itself (something that is provided in the windows flash) hence this being a trigger for heat build up.

EDIT: You could alsotry searching the software centre for progs to control the fan speed/cut in tmeps and see if you can set it to run more and see if that prevents the overheating.

---

### Post by pakkatechie on 2011-02-22
>                                                    Have you tried tweaking the settings in the bios regarding the fan cut in/safety cut out features?1564 Bios doesn't have any settings related fan

> When it crashes does it hang or does it shut itself down?Looks like crash. Screen goes blank, keyboard loses control and loud noise continously. Had to force shutdown. The logs doesn't have any info about this crash

> Flash is very intensive for CPUs on linux due to a lack of hardware  decoding ability in flash itself (something that is provided in the  windows flash) hence this being a trigger for heat build up.The problem is almost all sites have flash ads now a days. So just browsing for half an hour with site which has flash ads, make my laptop to crash. Great pain

> I ask this as somethimes lmsensor can not register things properly if some kernel modules arent present.coretemp addded in modules and hddtemp added in startup

---

### Post by seawolf167 on 2011-02-22
See if [this page ]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed")helps at all for turning on the fans.

Have you tried blowing out the case fans, heatsinks, vents, etc. to get rid of any dust buildups that may be causing overheating?

---

### Post by Sylos on 2011-02-22
> Looks like crash. Screen goes blank, keyboard loses control and loud noise continously. Had to force shutdown. The logs doesn't have any info about this crash

Hmmm. Not sure about this but I would expect that if excessive heat was causing problems then the protective measures on the MB would step in and shut the whole thing down. That usually means black screen with no noise - fans turn off as the whole unit powers off to protect from damage.

I would certainly agree with seawolf about trying to clean out all the vents and fans.

Has the system been ok in the past with 10.10 on it or has this always been a problem?

---

### Post by migs73 on 2011-02-22
Try this;

[http://ubuntuforums.org/showthread.php?t=1684657](http://ubuntuforums.org/showthread.php?t=1684657)

Haven't tried it myself yet though!!

---

### Post by FoxEWolf on 2011-02-22
try these:
 
sudo apt-get install i8kutils gkrellm gkrellm-i8k
 
sudo modprobe i8k force=1
 
sudo gedit /etc/modules
 
There is a file you need to edit somewhere but I do not recall where. I used to have an inspiron at my office, but now I have a Latitude E4600.
 
EDIT:
Here I placed a search on the forum here and I found the post tat explains where the file you need to edit is. 
 
[http://ubuntuforums.org/showpost.php?p=2374636&postcount=2](http://ubuntuforums.org/showpost.php?p=2374636&postcount=2)
 
Hope this helps!!

---

### Post by pakkatechie on 2011-02-23
> Syslos: Has the system been ok in the past with 10.10 on it or has this always been a problem?
It was less frequent in lucid. In maverick its unbearable

Hi _[FoxEWolf]("http://ubuntuforums.org/member.php?u=1248384")_
Thanks for searching and pointing me the post. Unfortunately i i8k, if i luanch i8kmon or other utils of i8k, it hangs. May be my model not supported for i8kutils

---

