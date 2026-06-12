---
title: "Bluetooth troubles - Can't get device information: Success"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by rdn2fst on 2007-05-31
**Mission: **
I am attempting to pair my motorola v3xx RAZR to my Fiesty Fawn in high hopes of using it as an internet connection.

**What I know: **
I know that i can use the phone as an internet connection because i have zero problems doing that now with a USB cable.  while the USB cable has its perks, it's still a cable and i like to be free and unbounded at times, which is why i am so set on getting this Bluetooth connection (pairing) to work.
[B]
Where I've been:[/B]
[http://ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+keyboard]("http://ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+keyboard")
[https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup")

**Status:**
I am unable to successfully connect my phone (as desired) with bluetooth.  However, i feel that I am very close to being able too and that the problem is simple.

**Details:**
[list]
[*]i can scan for devices and receive the 'bdaddr' or what looks to be a MAC address and the name of my phone.  ```
hachenbeak@Warsteiner:~$ hcitool scan
Scanning ...
        00:1B:52:CF:D8:5E       Aaron's Phone
```
[*]when i enter ```
hachenbeak@Warsteiner:~$ hidd --connect 00:1B:52:CF:D8:5E
``` the blue light flashes on my phone for a moment and then i receive ```
Can't get device information: Success
```
[*]My /etc/bluetooth/hcid.conf looks like:
```

root@Warsteiner:/home/hachenbeak# more /etc/bluetooth/hcid.conf 
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
device 00:1B:52:CF:D8:5E {
    name "Aaron's Phone";
    auth enable;
    encrypt enable;
}
root@Warsteiner:/home/hachenbeak# 

```
[/list]

help!  :)

---

### Post by wammin on 2007-07-12
I'm having the exact same problem! Someone help!

---

### Post by volkswagner on 2007-07-15
can't connect here.

I notice my hcid.conf has no reference to bluez pin manager as some other post request 

can i see somones hcid.conf with the bluez pin reference?

i also attached a portion of my syslog for when i 

```
hcid --connect <my mac address>
```

my guess is conflict with wifi or driver problem thinks my usb dongle is wifi not bt?

---

### Post by volkswagner on 2007-07-17
anyone with bluetooth working to post there hcid.conf file?

---

### Post by volkswagner on 2007-07-22
i am now able to share files via bt in both directions

not sure if it was python or just following the steps to send files.  ie right click>send>send via bt

i never tried any of this since i could not pair normally

try these steps in this thread [http://ubuntuforums.org/showthread.php?t=444233&page=2]("http://ubuntuforums.org/showthread.php?t=444233&page=2")

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

### Post by Scotty562 on 2007-08-06
I have the same phone as the original poster and the previous post worked great for me. Thanks!

---

### Post by corkyt on 2007-11-03
I just wanted to say, that I had the same problem as the OP, and this procedure didn't work, but another one I found somewhere else actually did!

If you go to "Bluetooth Preferences", click on the "Services" tab, then click on "Input service".  At the bottom click "Add".

You may see an empty popup window.  This is where you would have your phone broadcast ("Find Me", or "Connect" or w/e), then run "hcitool scan".

When "hcitool scan" is run, and the device is found, the device should appear in the popup window.  Simply "Connect" from this pop-up and then you'll be able to do the passkey handshaking and everything.

My guess is that it wasn't working because there is a bug in the BT software where it doesn't know how to handle passkeys so it only connects for a second before the connection drops.  Perhaps this can be solved by putting the passkey PIN in some config file, but this manual way worked for me.

---

