---
title: "bluez installed./.............. how to transfer data"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by rasesh_raz on 2007-08-02
how do i connect my phone to my computer usin bluetooth i have a running
bluez sfotware installed on my machine

---

### Post by rasesh_raz on 2007-08-02
i need help fast guys

---

### Post by volkswagner on 2007-08-02
Check out this thread> 

 Re: [IDEA] Better Bluetooth support.
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
__________________
Last edited by fmaste : 4 Weeks Ago at 03:27 PM. 

---

