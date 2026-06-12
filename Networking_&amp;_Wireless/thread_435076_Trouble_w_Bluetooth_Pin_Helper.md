---
title: "Trouble w/ Bluetooth Pin Helper"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by KyleYankan on 2007-05-06
Hi everyone, I'm having some troubles. I'm trying to set up my bluetooth on my new notebook (ell Inspiron E1405, with Dell Wirless 355). The Bluetooth works fine, just needs the occasional reset. However, whenever I launch kmobiletools, and my laptop tries to connect to my phone, I have some problems.

When the PC asks to bond with the phone, the phone asks for a pin. I enter such a pin, and about a minute later, I get "Invalid Pin" on my phone. My PC does nothing, other than after "Invalid Pin" starts scrolling "Input/output error"

Also, there's no such program as "bluepin" on my laptop, or in aptitude, and I'm on Feisty.

Here's my hcid.conf

```

#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attemptsc
	pairing multi;

        # PIN helper
        pin_helper /usr/bin/bluez-pin;
        #pin_helper /usr/bin/bluepin;
	#dbus_pin_helper /usr/bin/bluez-pin;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
```

---

### Post by KyleYankan on 2007-05-06
UPDATE:

I think the problem is dbus. I reinstalled it and bluez-* with synaptic and rebooted, but I'm still having the same problem: 

```
root@Brandy:~# hcid -n
hcid[7646]: Bluetooth HCI daemon
hcid[7646]: Unknown option 'pin_helper' line 24
hcid[7646]: syntax error line 24
hcid[7646]: Could not become the primary owner of org.bluez
hcid[7646]: Unable to get on D-Bus

```

---

### Post by RavanH on 2007-05-08
Sadly, I got the same problem on Feisty...

I had about the same hcid.conf file content because of alterations mentioned elswhere on this forum. I reverted these changes and ended up with the original file content:

> #
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

After running a bluetooth reset command in a terminal 
>  sudo /etc/init.d/bluetooth restart

This is the result:

> ravan@ravan-laptop:~$ hcid -n
hcid[16382]: Bluetooth HCI daemon
hcid[16382]: Could not become the primary owner of org.bluez
hcid[16382]: Unable to get on D-Bus

Can anyone tell me what is happening here and what can I do about it?

---

### Post by kitsos on 2007-05-22
I'm having a similar problem with dbus. Error as above, phone is found, it asks for password but fails to connect. Passkey 1234. Anybody that can help? plzzzzzzzz

---

### Post by undiaperfecto on 2007-05-29
I had he himself problem and it solves it of the following way

> sudo gedit /etc/bluetooth/hcid.conf

Set de security manager mode "auto"

> # Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
security auto;

Restart bluetooth services
> sudo /etc/init.d/bluetooth restart

Perdon por mi mal ingles ;)

---

### Post by dvo on 2007-06-23
This is how I got the PIN popup working for feisty: call (even as a normal user)
```
passkey-agent --default /usr/bin/bluez-pin
```
before initiating the connection. This will register bluez-pin as the pin helper,
as you may check with ```
tail -f /var/log/syslog
```

N.B. Including in /etc/bluetooth/hcid.conf a line like
```
pin_helper /usr/bin/bluez-pin;
```
does not help - for some reason, this option is not recognized any more :(

BTW, in order to make your machine visible for other BT devices, call (even as a normal user)
```
dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable
```

---

### Post by volkswagner on 2007-07-22
i am now able to share files via bt in both directions

not sure if it was python or just following the steps to send files. ie right click>send>send via bt

i never tried any of this since i could not pair normally

try these steps in this thread [http://ubuntuforums.org/showthread.php?t=444233&page=2](http://ubuntuforums.org/showthread.php?t=444233&page=2)

thanks to fmaste

Today almost every cell phone, notebook comes with bluetooth. There are lots of bluetooth mouse, headphones, remote controls, etc. I believe it is important to have good bluetooth support.
I know people that goes back to windows because of this things.

At least having something in System->Preferences that automatically installs the needed packages and let you configure bluetooth and search for devices.
With the help of the Ubuntu community we can develop something.
This is what I did to have bluetooth on my DELL inspiron 9400 that may be useful, it can be done automatically.

On a terminal type:
sudo apt-get install gnome-bluetooth bluez-gnome python-bluez python-libbtctl bluez-utils bluez-gnome
Now "Bluetooth File sharing" will appear under Applications->Accesories, once activated a new icon will appear near the clock to identify it.
To execute it automatically at startup, go to System->Preferences->Session-> Startup Programs, click on new and type gnome-obex-server.
Restart your computer. (Maybe doing something else this won't be needed)
You will also have under System->Preferences->Bluetooth preferences some extra configuration to play with to make you cellphone, etc work.
To search for bluetooth devices:
Make the device discoverable (look for a "Connect" button on many keyboards and mice or look in the device's manual) and then search for the device with this command:
sudo hidd --search
If that command doesn't work, try this one:
hcitool scan
Hint: If no devices are being shown and you are using Edgy Eft (6.10), you may try
sudo hciconfig hci0 inqmode 0
See bug [[https://launchpad.net/ubuntu/+source...th/+bug/70718]](https://launchpad.net/ubuntu/+source...th/+bug/70718]) #70718. If this helps, you may add the hciconfig command (without "sudo") to your /etc/rc.local file for a permanent workaround.
To change the location that files are saved to when using bluetooth transfers
gconf-editor
Then navigate to
/apps/gnome-obex-server
where you can specify the save directory and also turn off that annoying dialogue box!

---

