---
title: "Bluetooth not working AT ALL on Thinkpad T61"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by sancho panza on 2007-10-26
Bluetooth is not working AT ALL on my laptop. It is almost as if my laptop does not have bluetooth. I know it should have, cos I paid for it ;)

Anyhow, I have a Thinkpad T61 and a Nokia cellphone. I tried following all the posts in this forum and the community help files and the thinkwiki files, but no matter what I install, my cellphone does not see my laptop. The cellphone works fine bcos I have paired it with other windows machines earlier. The programs installed do not show any error messages at all. They just cannot detect anything.

Outputs:
```
hcitool scan
Device is not available: No such device 
```
```
hcitool dev
Devices:

```

Any ideas?

---

### Post by luistorresmx on 2007-10-27
Same problem on a Compaq, no answer yet :(

---

### Post by kraftey on 2007-10-27
Same problem here on an asus F3 series... can't find an answer anywhere else.

---

### Post by sancho panza on 2007-10-30
Bump...

---

### Post by John Jason Jordan on 2007-11-01
> **sancho panza said:**
> Bluetooth is not working AT ALL on my laptop. It is almost as if my laptop does not have bluetooth. I know it should have, cos I paid for it ;)

Anyhow, I have a Thinkpad T61 and a Nokia cellphone. I tried following all the posts in this forum and the community help files and the thinkwiki files, but no matter what I install, my cellphone does not see my laptop. The cellphone works fine bcos I have paired it with other windows machines earlier. The programs installed do not show any error messages at all. They just cannot detect anything.

Outputs:
```
hcitool scan
Device is not available: No such device 
```
```
hcitool dev
Devices:

```

Any ideas?
I have it sort of working on my T61 with Gutsy amd64. That is, when I turn on the bluetooth in my Morotola Razr and then do "hcitool scan," if finds the phone. However, I can't find any GUI in Gutsy to scan for the phone, nor have I tried actually transferring files or anything.

What I really want to do eventually is use bluetooth headphones for listening to streaming stereo from my laptop. But before I buy a set of expensive headphones I want to figure out that it is possible to do so. The Motorola phone is just my first step because I already had it in my pocket.

---

### Post by MeanderingCode on 2007-12-27
Why is there no activity in this thread??????

I have a thinkpad t40p with a bluetooth card that doesn't seem to exist, either.
I *know* it is there, though.

WHY is there no info about this except in this thread of commiserating folk?

---

### Post by zonky on 2007-12-27
many laptops do have external, physical switches which limit bluetooth and/or wireless devices being on or of.

Have the posters above looked the manual to see if there is a seperate bluetooth control?

---

### Post by MeanderingCode on 2007-12-27
Okay.  I'm a liiiiitle bit pacified.

On thinkwiki.org, i found [this]("http://www.thinkwiki.org/wiki/ThinkPad_Bluetooth_with_Enhanced_Data_Rate_(BDC-2)") page.

Synopsis:
Check if thinkpad_acpi module is loaded:
```
lsmod | grep acpi
```
The the wiki says that if Fn+F5 doesn't work (didn't for me), to run this with root privileges:
```
echo "enable"> /proc/acpi/ibm/bluetooth
```
I couldn't do this simply by prefixing with sudo.  I got a "permission denied" error.
So i used su to become root on the command line, and it worked!  I'm not sure why.  If anyone knows, i'd be delighted to hear it.

Well, now to explore ways of turning it on/off.
I found [this]("http://ubuntuforums.org/showthread.php?t=406752") thread...well, post, really, but have yet to dig into it, ergo i do not know why it didn't work for him.

---

### Post by mathcharbe on 2007-12-30
I have a thinkpad T61 7664 16U
I have the exact same problem with my bluetooth. The only thing I found to enable it is to go as root and use " echo enable > /proc/acpi/ibm/bluetooth". And then, I was not able to get a good connection with my cell phone.
With sudo instead of root, I get the message "bash: /proc/acpi/ibm/bluetooth: Permission denied"
Could it be a permission problem??
Is it NOT working only on thinkpads?

Thanks

---

### Post by MeanderingCode on 2007-12-31
> **mathcharbe said:**
> I have a thinkpad T61 7664 16U
I have the exact same problem with my bluetooth. The only thing I found to enable it is to go as root and use " echo enable > /proc/acpi/ibm/bluetooth". And then, I was not able to get a good connection with my cell phone.
With sudo instead of root, I get the message "bash: /proc/acpi/ibm/bluetooth: Permission denied"
Could it be a permission problem??
Is it NOT working only on thinkpads?

Thanks

Check out my above post.  I'm on a thinkpad T40p.
I don't know about "a good connection", but it works for me just fine (with my cell phone)

---

### Post by sancho panza on 2008-01-02
Thanks for digging up this thread guys, I have been quite busy of late to follow up on this.
My apologies.

---

### Post by Whiffle on 2008-01-02
Hmm, works flawlessly on my T43 w/ KDE.  First of all, is the bluetooth light under the screen lit up?

---

### Post by mathcharbe on 2008-01-08
Yes, the LED turns on when using 
echo enable > /proc/acpi/ibm/bluetooth
when you are root.

---

### Post by eichin on 2008-01-29
> **MeanderingCode said:**
> run this with root privileges:
```
echo "enable"> /proc/acpi/ibm/bluetooth
```
I couldn't do this simply by prefixing with sudo.  I got a "permission denied" error.
So i used su to become root on the command line, and it worked!  I'm not sure why.  If anyone knows, i'd be delighted to hear it.


A common annoyance: when you run that with sudo, *your* shell tries to do the redirection, and then call sudo with that file open as standard output.  This doesn't work (so it doesn't even try to run sudo, the "permission denied" is from your shell.

An easy-to-remember workaround I picked up somewhere is to use "tee":
```
echo enable | sudo tee /proc/acpi/ibm/bluetooth
```

(which worked for me just now - I came looking for this because I just noticed it not working, even though I don't think I needed it in Dapper - well, at least this default saves some battery life :-)

---

### Post by diegosacchetti on 2008-02-02
> **MeanderingCode said:**
> Okay.  I'm a liiiiitle bit pacified.

On thinkwiki.org, i found [this]("http://www.thinkwiki.org/wiki/ThinkPad_Bluetooth_with_Enhanced_Data_Rate_(BDC-2)") page.

Synopsis:
Check if thinkpad_acpi module is loaded:
```
lsmod | grep acpi
```
The the wiki says that if Fn+F5 doesn't work (didn't for me), to run this with root privileges:
```
echo "enable"> /proc/acpi/ibm/bluetooth
```
I couldn't do this simply by prefixing with sudo.  I got a "permission denied" error.
So i used su to become root on the command line, and it worked!  I'm not sure why.  If anyone knows, i'd be delighted to hear it.

Well, now to explore ways of turning it on/off.
I found [this]("http://ubuntuforums.org/showthread.php?t=406752") thread...well, post, really, but have yet to dig into it, ergo i do not know why it didn't work for him.

>>>>>>>>>>>
I had the same problem on T41 and with that procedure it worked !

---

### Post by lmarr28 on 2008-02-06
Hey, guys...  I was having the same problem with Fn+F5 not working on my T41 (with Gutsy) until I found [this page]("http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth#Enabling_Bluetooth").  After making this change, Fn+F5 works perfectly!

Basically, to make it start working in Gutsy, edit **/etc/acpi/ibm-wireless.sh** and comment-out the line: **"if ! isAnyWirelessPoweredOn; then"** and it's corresponding **"fi"** (see example below).

```

#!/bin/sh
# Find and toggle wireless of bluetooth devices on ThinkPads

. /usr/share/acpi-support/state-funcs

BLUETOOTH=/proc/acpi/ibm/bluetooth

if [ -r $BLUETOOTH ]; then
    grep -q disabled $BLUETOOTH
    bluetooth_state=$?
fi

# Note that this always alters the state of the wireless!
toggleAllWirelessStates;

# Sequence is Both on, Bluetooth only, Wireless only, Both off
# if ! isAnyWirelessPoweredOn; then
    # Wireless was turned off
    if [ -w $BLUETOOTH ]; then
        if [ "$bluetooth_state" = 0 ]; then
            echo enable > $BLUETOOTH;
        else
            echo disable > $BLUETOOTH
        fi
    fi
# fi

```

:guitar:

---

### Post by sancho panza on 2008-03-27
Thought I'll just bump this thread as I'll be trying to get bluetooth to work in hardy sometime soon...Do keep us posted if you have any updates on how bluetooth on thinkpad works with Hardy.

Cheers!

---

### Post by Whiffle on 2008-03-27
Heres a quick overview of acpi/bluetooth/etc and some scripting.  Its pretty quick and dirty really, but hopefully it'll shed some light.  

Okay here is how I have mine setup.  By default (in theory), on ubuntu, on a thinkpad, it is setup so that pressing Fn+F5 (or whatever your wireless button is), it toggles through various states of BT being on, Wifi being off, BT being off, Wifi Being on, and both being on.  I thought this was kind of silly, since right next to the wireless button on my laptop, is Fn+F6, another perfectly good ACPI-event generating function key without any use.  So, I set it up so that Fn+F5 toggles only my wireles,s and Fn+F6 toggles only my Bluetooth.  It works so slick it should be illegal.  Here's a quick overview of how the whole system works.
 
There are four main pieces that need to be in place to use the bluetooth on a thinkpad.  There is the thinkpad_acpi module, the bluetooth modules, and the services needed to run it, and the userspace tools.

First, bluetooth on the thinkpads is controlled by the thinkpad_acpi kernel module.  Make sure this is loaded first, otherwise nothing will work.  To check, do
```

lsmod | grep thinkpad_acpi

```
It should be listed, if so, you're in good shape there.

Next, the bluetooth hardware is switched on and off is by writing either "enable" or "disable" to the file **/proc/acpi/ibm/bluetooth** That takes care of turning it on and off at the hardware level.

Once the bluetooth is activated, there are a couple of kernel modules that need to be loaded in order for bluetooth functionality to work.  I don't know off the top of my head what they are, but when I run
```

lsmod | grep bluetooth

```
this is what I get:
```

bluetooth              50532  7 hci_usb,rfcomm,l2cap

```
These are all needed for bluetooth to work, and theoretically should load automatically.  If not, you'll need to do it.

Next, there is the bluetooth service.  Assuming it is installed ( you can probably search for it in synaptic), it can be started by doing (off the top of my head)
```

sudo /etc/init.d/bluetooth start

```

Now, thats kind of a quick and dirty outline of how bluetooth supposed to work, hopefully its enough to get you on the right foot if its not working.  The final part is the ACPI scripting involved in turning bluetooth and WiFi on and off.  This works as follows.  When the acpid service starts, it checks through the **/etc/acpi/events/** directory.  In this directory contains a series of files, named loosely after what they do.  They basically say "If this ACPI event happens, do this action".  For example;
```

event=ibm/hotkey HKEY 00000080 00001005
action=/etc/acpi/ibm-wireless.sh

```
That event corresponds to the key combination Fn+F5 being pressed.  When that happens, it runs the script /etc/acpi/ibm-wireless.sh.  Nice and simple.  The thing to remember here is that if you change any of these actions, you must restart the acpid service for them to take effect.  This can be done with
```

sudo /etc/init.d/acpid restart

```
The possibilities here are endless.  You can take any ACPI event, and use it to do pretty much any function.  If you'd like to find out what event a button produces, you can run the **acpi_listen** program, and then press buttons.  Be sure to shut down the acpid service if you're pressing buttons that normally do things such as shut off the computer,  More information on this can be found here:
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work)

Here is how I have my wifi/bluetooth setup.  They each have a file in the events folder, and they each have their own toggle script:

/etc/acpi/events/ibm-bluetooth
```

event=ibm/hotkey HKEY 00000080 00001006
action=/etc/acpi/bluetooth.sh

```

/etc/acpi/events/ibm-wireless is the example I put up above.  

These call the following two scripts:
/etc/acpi/bluetooth.sh
```

#!/bin/bash
#toggles the state of bluetooth

BLUETOOTH=/proc/acpi/ibm/bluetooth

if [ -r $BLUETOOTH ]; then
    grep -q disabled $BLUETOOTH
    bluetooth_state=$?
fi

    if [ -w $BLUETOOTH ]; then
        if [ "$bluetooth_state" = 0 ]; then
            echo enable > $BLUETOOTH;
        else
            echo disable > $BLUETOOTH
         fi
    fi

```

 I also have it a little fancier on mine to where it loads and unloads the required kernel modules, and starts/stops the bluetooth service.  Its kind of experimental at this point and I left it out for the sake of simplicity.  If you'd like to mess with it, i'd be glad to help.  This script is actually adapted/borrowed/copied from a bluetooth script that came on my feisty install.

Next is the wireless script, 
```

#!/bin/bash
#toggle wireless
. /etc/acpi/acpi-support/state-funcs

startWifi()
{
sleep 2
echo -n $ON > $CONTROL
/etc/rc.d/wicd start
return 1
}

stopWifi()
{
echo -n $OFF > $CONTROL
/etc/rc.d/wicd stop
return 1
}

toggleAllWirelessStates()
{
    for DEVICE in /sys/class/net/* ; do
        if [ -d $DEVICE/wireless ] ; then
            # $DEVICE is a wireless device. Check if it's powered on:
            ON=0
            OFF=1  # 1 for rf_kill, 2 for power/state
            for CONTROL in $DEVICE/device/rf_kill $DEVICE/device/power/state ; $
                    # We have a way of controlling the device, lets try
                    if [ "`cat $CONTROL`" = 0 ] ; then
                        # It's powered on. Switch it off.
                        if stopWifi; then
                            break
                        else
                            OFF=2 # for power/state, second time around
                        fi
                    else
                        # It's powered off. Switch it on.
                        if startWifi ; then
                            break
                        fi
                    fi
                fi
            done
        fi
    done
}

toggleAllWirelessStates;

```

This is yet another script I borrowed from Fiesty and then hacked up.  It just toggles the state of my wireless using the rf_kill switch, and shuts off or starts the wicd daemon.  It isn't directly compatable with ubuntu, but its a decent example.  I'd like to clean it up a bit though, and maybe make it load/unload drivers and such.  

If theres enough interest I'll clean this up and turn it into  a more formal and comprehensive HOWTO, I just typed this between homework assignments...maybe even to relax? :confused:

---

### Post by sancho panza on 2008-04-27
Thanks for posting on this thread guys. The problems has been solve in Hardy. 

Press Fn+F5 one to three times (it cycles thru Bluetooth > Bluetooth+wireless > wireless) to enable bluetooth. Thats it. Then right-click on the bluetooth icon in the notification panel to tweak settings. My cell phone can then detect the laptop.

Cheers!

---

### Post by Clunky tech on 2008-06-02
Dont know if this will help any of you but here goes.
I couldnt get bluetooth to work on my T61. Network was switched on buy FN+F5 would not work at all.

I did a search on my machine using "bluetooth" (without comas) as the search string. I found a directory (C:\Business\Drivers\Bluetooth\BCBTUM 5.1.2535.0) with all the bluetooth set up files therin. I ran the setup.exe file and bingo. The bluetooth activated found all the hardware and I can now see my phones and even my GPS reciever.

---

