---
title: "how to disable bluetooth on startup?"
date: 2018-08-15
forum: Networking &amp; Wireless
---

### Post by loewenblum on 2018-08-15
hello community  ):P

When I start my lubuntu (ubuntu 18.04.1 lts) I always have to manually turn off the bluetooth connection. 
Is there a way to turn it off completely, so that it doesn't start again?

I couldn't find a working solution in the internet.
Maybe you could help.

best regards,
loewenblum

---

### Post by aromo2 on 2018-08-15
```
sudo systemctl disable bluetooth --now
```

---

### Post by #&amp;thj^% on 2018-08-15
To go along with aromo2's suggestion: to deactivate bluetooth on startup run this
```

sudo systemctl disable bluetooth.service
```

then on next reboot bluetooth will not be active ... to view status issue
```

sudo systemctl status bluetooth.service
```

to activate bluetooth on startup run this
```

sudo systemctl enable bluetooth.service
```

---

### Post by loewenblum on 2018-08-16
thank you, it works!

---

### Post by laslozr on 2018-09-17
Hi there,

For me it didn't work just to disable bluetooth with the following code: ```
[COLOR=#000000][FONT=&quot]sudo systemctl disable [/FONT][/COLOR][COLOR=#417394][FONT=&quot]bluetooth[/FONT][/COLOR][COLOR=#000000][FONT=&quot].service[/FONT][/COLOR]
```, because after a restart, bluetooth was enabled again.

I found and alternative solution, and that would be the following (I use nano, feel free to use any other text editor):

Step 1:
Navigate to the folder: ```
/etc/systemd/system/
```
Step 2:
First create a script that will kill the bluetooth service once run:
```
nano bluetoothkill.sh
```

Step 3:
Instert the following script:
```

#!/bin/bash
rfkill block bluetooth
exit 0

```

Step 4:
Create a foo.service file in the same folder ```
/etc/systemd/system/
``` :
```
nano foo.service
```



Step 5:
Insert the following script:
```

[Unit]Details=Additional startup scripts
After=network.target


[Service]
ExecStart=/etc/systemd/system/bluetoothkill.sh


[Install]
WantedBy=default.target

```
[FONT=Verdana]
Step 6:
Run the following command in the terminal:
```
[/FONT]sudo systemctl start foo.service
```

Step 7:
Restart the machine and on the next boot you will notice that the Bluetooth service is no longer enabled by default on startup. You can still enable it when ever you like in the settings, or the terminal it is behaving without any errors.

If you like to add more scripts on startup, you can always edit the ```
foo.service
``` file and add additional lines under the [Service] bracket to run additional scripts on startup, for example:
```

ExecStart=/full-script-filepath/newscript.sh

```

---

### Post by saunders8669 on 2018-10-06
Thanks, works great :D

---

### Post by praseodym on 2018-10-06
Why not simply blacklisting the BT driver instead of deeply manipulating the system?!

---

### Post by Qew on 2018-10-06
This is like laslozr's suggestion, but with less steps.

Using sudo, open this file in your favourite text editor: **/etc/rc.local**

Below the commented out text (lines starting with #) and above the line that has "exit 0", add the following:

```
rfkill block bluetooth
```

If you haven't edited this file before, then it should look like this after your change:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rfkill block bluetooth
exit 0

```

Save and then reboot.

To re-enable Bluetooth, you just flip the switch in Settings or in the Status Area dropdown. This way there's no need for sudo commands in the terminal to use Bluetooth when you need it. The above just turns off Bluetooth's state on start-up, but allows you to re-enable it. This has worked for me in 16.04 and 18.04.

---

### Post by noexcuse on 2018-12-13
Your solution worked with me, with a tweak. I have Ubuntu 18.04 LTS and there is no etc/rc.local file or folder. However, there is a Bluetooth folder in etc. Inside there is input.conf file. I wrote there the code at the end, like this:

```
# Configuration file for the input service

# This section contains options which are not specific to any
# particular interface
[General]


# Set idle timeout (in minutes) before the connection will
# be disconnect (defaults to 0 for no timeout)
#IdleTimeout=30


# Enable HID protocol handling in userspace input profile
# Defaults to false (HIDP handled in HIDP kernel module)
#UserspaceHID=true


rfkill block bluetooth
exit 0
```

And bluetooth is turned off at start-up and can be turned on from settings.

---

### Post by Qew on 2018-12-15
Good that you got it working. Mind you, I'm not sure you need the "exit 0" at the end, as that file isn't a script, it's just a conf file.

Also, I learnt that 18.04 LTS doesn't come with /etc/rc.local now, but I also learnt that if you add /etc/rc.local, make it executable, and add "#!/bin/sh -e" on the first line and "exit 0" on the last, then it'll work as I mentioned above. It came with 16.04, which I upgraded from to 18.04, hence why I've still got it and it works for me. I didn't know that rc.local isn't in use by default in 18.04, so good to learn something new. Cheers!

More info here (this is for 16.10, but works for 18.04): [https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10](https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10)

---

### Post by duncanka2 on 2018-12-16
There's a much simpler method: just open [FONT=courier new]/etc/bluetooth/main.conf[/FONT] and change the last line to [FONT=courier new]AutoEnable=false[/FONT].

Bluetooth is then disabled at startup, but can be re-enabled from settings.

I believe this should also work on any Linux installation with bluez, though I've only tested it in Ubuntu 18.10.

---

### Post by Qew on 2018-12-18
Unfortunately, at least for me and my 18.04 setup, that doesn't seem to work well. If I have Bluetooth set to on and I reboot, then Bluetooth is still on after reboot, when I'd expect it to be off. I do have Bluez installed. Yes, I returned rc.local back to its default state and edited /etc/bluetooth/main to what you said before testing it out, yet it didn't work as I expected. I put it back to what I had before (editing rc.local), and now it works as expected.

Still, maybe it'll work for others. I'll try again when I upgrade to the next LTS (I'll try to remember ;) ).

Edit: Thinking about it a bit more, maybe the fix above mentioned by duncanka2 is working, it's just not in the way I want it to, so it's more my problem than anything else. I suppose auto-enabled isn't the same as enabled. If I manually turn it on, then it's not really *automatically* turned on if it's still on after the next boot, it's just sticking to what I set it as beforehand. So, the setting is probably working as intended.

---

