---
title: "Avoid putting computer to sleep while program runs in a terminal window"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Jensen39 on 2010-08-31
Dear All

Short description: I would like to be able to run a program in a Terminal window until it has finished without the computer going to sleep mode, but after the program has finished it should follow the "Power Management" settings.

Long description: I am new to Ubuntu so I am not sure if I have described my problem in an understandable way. I have numbered the steps to help explaining what I do.

1) I want to have a short "Power Management" setting of 10 minutes since I would like to use as little electricity as possible, under System, Preferences, Power Management, "On AC Power". I also use a screen saver, set for 5 minutes, under System, Preferences, Screensaver.

Note: My computer is an older model and uses quite a lot of electricity, but it runs Ubuntu 10.04 without any problems at all.

2) Then I start a program in a Terminal window (Applications, Accessories, Terminal) and start a program e.g. converting an sound MP3 I have made myself to an M4A file to create an Audio book. I can do this using only a text command.

3) I then leave the computer.

4) What happen now is that the screen saver starts after 5 minutes (showing a blank screen) and the computer goes to sleep after 10 minutes stopping the running program in the terminal window.

5) If I then touch the keyboard the screen and computer comes out of sleep and continues the Terminal window program. The terminal window continues the program without any errors and everything works normally.

6) If I set the "Power Management" to "Never" under System, Preferences, Power Management, "On AC Power" and go to bed, then it completes the command in the Terminal window within a few hours. Unfortunately then the computer is turned on for several hours unneeded until I wake up in the morning.

So somehow I would like to tell Ubuntu that it should use the Screensaver the way it does now but wait until the Terminal window program has finished before it starts the "Power Management" 10 minutes stopwatch.

Unfortunately I cannot just go out and buy a new computer using less electricity but I am saving up for it and will compare computer models when I get that far.

Thanks in advance.

Best Regards
Jensen39

---

### Post by mike555 on 2010-08-31
try " Caffeine", it can be set for time .

---

### Post by viralmeme on 2010-08-31
> **Jensen39 said:**
> Short description: I would like to be able to run a program in a Terminal window until it has finished without the computer going to sleep mode, but after the program has finished it should follow the "Power Management" settings.

Try this [Disable Power Saving]("http://ubuntuforums.org/showthread.php?t=1122909") Script.

---

### Post by freak42 on 2010-08-31
try this on the commandline

```
gnome-power-manager-inhibit ##yourcommandOrScriptHere##

```

---

### Post by Jensen39 on 2010-09-01
Hi All

Thank very much for your fast reply. This is the first time I have tried to ask a question in an Ubuntu forum and I am impressed. 

I will try all 3 methods and post back with the result. It make take a few days to test them all since I am new to this.

Thanks again

:) Jensen39

---

### Post by Jensen39 on 2010-09-03
Hi All

I have tried the surgestions and it works - in several ways. In order to try to help other beginners I go through them in detail and show what I did.

gnome-power-manager-inhibit ##yourcommandOrScriptHere##:

The surgestion by freak42 I cannot find out how to use. I have found that under
/usr/bin on Ubuntu 10.04 I do not have that command. However I did find a reference :
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/419829](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/419829)
Titled "gnome-power-manager-inhibit gone in karmic" that says that this script was removed in Karmic and there is a reference to an explanation as to why. The reference to the explanation is beyond my Ubuntu skills though.

gnome-screensaver-command -i

viralmeme showed the way to a reference:
[http://ubuntuforums.org/showthread.php?t=1122909](http://ubuntuforums.org/showthread.php?t=1122909) where FuturePilot has an elegant solution.
  For help with && see:
  [http://ubuntuforums.org/showthread.php?t=650634](http://ubuntuforums.org/showthread.php?t=650634)
  For help with "killall -15" see:
  [http://ubuntuforums.org/showthread.php?t=121364](http://ubuntuforums.org/showthread.php?t=121364)

The reference shows how to disable sceensaver and power-manager in a script. I will show a little simpler version of how to use the method since my script skills are lagging quite behind FuturePilot (no pun intended).

First I create a test script by first creating a file "test_no_power_mgr"
using an editor, in my case gedit (Applications, Accessories, gedit) and
insert the text:

# Method adopted from: [http://ubuntuforums.org/showthread.php?t=1122909](http://ubuntuforums.org/showthread.php?t=1122909)
# Diable screensaver and power manager settings. The & starts the command
# in the background.
/usr/bin/gnome-screensaver-command -i &
# Using the unix sleep command twice as an example of using several commands.
# Get documentation for the sleep command with "man sleep" in a terminal window.
# It instead of the sleep commands I will insert my long running program commands.
sleep  ;
sleep 3 ;
# Stop the background process gnome-screensaver-command.
# For "killall -15" reference see [http://ubuntuforums.org/showthread.php?t=121364](http://ubuntuforums.org/showthread.php?t=121364)
# or "man killall" in a terminal window.
killall -15 gnome-screensaver-command ;

Then save the script and make the file executable by using the command
chmod 700 test_no_power_mgr

I then execute the script using:
./test_no_power_mgr

Caffeine:

The solution from mike555 is quite advanced.
I got the installation instructions from:
[http://www.omgubuntu.co.uk/2010/05/ubuntu-lucid-icons-for-caffeine.html](http://www.omgubuntu.co.uk/2010/05/ubuntu-lucid-icons-for-caffeine.html)

sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt-get update
sudo apt-get install caffeine

After that "man caffeine" gives a manual but I include a rough example below.

I then started the program from Applications, Accessories, Caffeine
A small coffee cup now appears to the right in my toolbar at the top of the screen.
Right click on it and select Preferences.
Marked "Start Caffeine on login"
Close

The point is that by just clicking on the coffee cup it can prevent screensaver and power saving in two ways:
1) Right click and select "Activate for" a fixed interval can be choosen e.g. 10 minutes. So that in the future just single clicking on the icon, power management and screen saver is disabled for 10 minutes.

2) Right click and select "Preferences". Now we can select a process that will always result in disabling screensaver and power management. This is done by pressing Add and either selecting from a "Running Processes" or "Resent Processes" tab. I started the program I wanted to add from a terminal window, used "Running Processes", clicking on the pane title alphabetizes the processes and finding the program I wanted, selected it and pressed "Add".


Conclusion: 
The "gnome-screensaver-command -i" works in scripts and Caffeine works for often used programs and just for a fixed time interval.

All in all this makes it possible to solve my problem perfectly.

And with regards to the fact both also disable the screensaver then the good old screen saver "power off" on the side of the monitor still works :)

Again thanks a lot for helping me.

Best Regards and have a nice weekend
:) Jensen39

---

