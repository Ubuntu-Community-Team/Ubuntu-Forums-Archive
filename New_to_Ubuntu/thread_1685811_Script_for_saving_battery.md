---
title: "Script for saving battery"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by pranavk_uict on 2011-02-11
I visited LessWatts.org which tells many tricks and tips to save the battery. Now what I want to do is to write a script that will run everytime I unplug my AC adaptor from my laptop. I know the actual commands which I can put in a terminal and they work fine. But I am not able to get them into a script. Please tell me how I can convert all these commands into a script and make them executable (and put it where??) so that it will run everytime I plug-off and plug-on the AC power


(The 1st line of the code tells you what I do when on battery power and the second line specifies command for when AC power)
**1. Disable bluetooth**
```
sudo hciconfig hci0 down
``````
sudo hciconfig hci0 up
```[B]
2. Disable wake on LAN[/B]
```
sudo ethtool -s eth0 wol d
``````
sudo ethtool -s eth0 wol g
```**3. Enable Advanced Power Management**
```
hdparm -B 1 -S 12 /dev/sda
``````
hdparm -B 255 /dev/sda
```**4. Disable cdrom polling**
```
sudo hal-disable-polling --device /dev/scd0
``````
sudo hal-disable-polling --device /dev/scd0 --enable-polling
```**5. Disable atime and enable diratime**
```
sudo mount -o remount,noatime   /
``````
I am not sure what exactly should be here to enable atime as it was originally
```Also, please give any other suggestions that can be included in this script to save batter power. I dont want to disable compiz though.

The original site which helped me find these commands is
[http://www.lesswatts.org/](http://www.lesswatts.org/)

---

### Post by Skerit on 2011-02-11
You should take a look at the events in

/etc/acpi/events

These are all files that contain an event and an action.
Take a look at the battery event file:

```
# /etc/acpi/events/battery
# Called when AC power goes away and we switch to battery

event=battery
action=/etc/acpi/power.sh

```

You can simply copy this, give it another name, and redirect the action to the script of your liking.

Be careful, though, I made the most basic of scripts (it sends a "notify-send test" command) when the battery takes over, and it runs in an infinite loop. I have NO idea why.

---

### Post by pranavk_uict on 2011-02-13
Thanks for your help about where to place the script. But I also need help about how I can write a script file when I dont know much about it and just know what commands it should execute in terminal like I have mentioned in the post before. Please help with the script file

---

