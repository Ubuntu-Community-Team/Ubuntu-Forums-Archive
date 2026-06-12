---
title: "hanvon"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by jasonrisenburg on 2011-08-23
I got a hanvon graphic tablet for my birthday, and it is not supported by the company. I have tried the easy stroke and tried to use the drivers it came with in wine ( desperate), but still no luck. I have always fumbled through bash and sometimes reinstalled. where should I start, to try to develop a driver?

---

### Post by Favux on 2011-08-23
Hi jasonrisenburg,

I assume it is usb.  Does it show up in *lsusb*?  That would indicate there is a driver for it in the kernel.

Otherwise you could look at [http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/](http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/)  from ondrah [http://ubuntuforums.org/showthread.php?t=1178978](http://ubuntuforums.org/showthread.php?t=1178978)  That's suppose to be the kernel usb driver/module component I think.  Don't know what X driver is suppose to be used.  Evdev should pick it up if it shows up in *lsusb* and *xinput list*.  Whether it will work with evdev is another question.

---

### Post by jasonrisenburg on 2011-08-23
daffy@daffy-laptop:~$     lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0b57:8037 Beijing HanwangTechnology Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

I think it is the beijing one, now to figure out how to use it..lol, well it is a start, off to google. If there is any thoughts ......

---

### Post by Favux on 2011-08-23
Alright good, a Hanwang not a Havnon.
> Bus 007 Device 002: ID 0b57:8037 Beijing HanwangTechnology Co., Ltd 
Vendor ID = 0b57  Product ID = 8037

Hangwang's are suppose to use the Wacom X driver.  I assume they already have a kernel driver.  So we need to check on the keywords.  Post the output of:
```
xinput list
```
in a terminal.  What release of Ubuntu are you using?

---

### Post by jasonrisenburg on 2011-08-23
daffy@daffy-laptop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]
daffy@daffy-laptop:~$

---

### Post by Favux on 2011-08-23
Hmmm.  Tablet's not there.  OK, what is the output of?
```
grep -i name /proc/bus/input/devices
```
And which release of Ubuntu?  Natty (11.04) or Lucid (10.04) or what?

---

### Post by jasonrisenburg on 2011-08-28
thanks I use ubuntu 11.04, and 

daffy@daffy-laptop:~$ grep -i name /proc/bus/input/devices Ubuntu 11.04
/proc/bus/input/devices:N: Name="Lid Switch"
/proc/bus/input/devices:N: Name="Power Button"
/proc/bus/input/devices:N: Name="Sleep Button"
/proc/bus/input/devices:N: Name="AT Translated Set 2 keyboard"
/proc/bus/input/devices:N: Name="Dell WMI hotkeys"
/proc/bus/input/devices:N: Name="PS/2 Mouse"
/proc/bus/input/devices:N: Name="AlpsPS/2 ALPS GlidePoint"
/proc/bus/input/devices:N: Name="Video Bus"
/proc/bus/input/devices:N: Name="HDA Intel Mic at Ext Right Jack"
/proc/bus/input/devices:N: Name="HDA Intel HP Out at Ext Right Jack"
grep: Ubuntu: No such file or directory

---

### Post by Favux on 2011-08-28
So the tablet isn't listed.  OK, check in the Software Center or Synaptic Package Manager that xserver-xorg-input-wacom is installed.  If not install it.  If it is check in /usr/share/X11/xorg.conf.d for the file 50-wacom.conf.  Post the contents of that file.

---

### Post by jasonrisenburg on 2011-08-30
here it is, I see it says hanwang there.


Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

---

### Post by Favux on 2011-08-30
Hmmm.  If the xf86-input-wacom driver is installed and you have the correct usb snippet in the wacom.conf why isn't it matching?

Let's see if it is showing up in your Xorg.0.log and if that tells us anything.  That file is in /var/log.  It's big so to compress it right click on it and use Create Archive.  Then attach it to your next post with Manage Attachments below.

---

### Post by jasonrisenburg on 2011-08-30
i hope this is ok, it didnt have that option so i googled it and it said to do this.

---

### Post by Favux on 2011-08-30
Alright, nothing in Xorg.0.log.  So it isn't that the Wacom X driver is rejecting the tablet.  I'm thinking this means the problem is in the Hanwang kernel driver/module.

The Hanwang isn't in the 2.6.36 kernel source code.  I have a git clone of I think the 2.6.38 kernel and that does have the hanwang.c file.  Looking at the defines I can verify the vendor:
```
#define USB_VENDOR_ID_HANWANG		0x0b57
```
This may be the problem here:
```
static const struct hanwang_features features_array[] = {
	{ 0x8528, "Hanwang Art Master III 0906",
	  ART_MASTERIII_PKGLEN_MAX, 0x5757, 0x3692, 0x3f, 0x7f, 2048 },
	{ 0x8529, "Hanwang Art Master III 0604",
	  ART_MASTERIII_PKGLEN_MAX, 0x3d84, 0x2672, 0x3f, 0x7f, 2048 },
	{ 0x852a, "Hanwang Art Master III 1308",
	  ART_MASTERIII_PKGLEN_MAX, 0x7f00, 0x4f60, 0x3f, 0x7f, 2048 },
};
```
since your model (product ID = 8037) isn't in there.  If I'm correct that would mean it needs to be added before compiling the module.  The hanwang.c file is in the kernel's /drivers/input/tablet directory.

---

### Post by PoppyX on 2011-08-30
Hi

Im new using Ubuntu. And i have just install Ubuntu on my Laptop HP G62-455DX.

The visual effects and others things arent working, i need some help pls.

And i dont know how to manage the System Preferences.

Thx

---

### Post by Favux on 2011-08-30
Hi PoppyX,

Welcome to Ubuntu forums!


[SIZE="4"]**Moderators.  Please move PoppyX's post to a separate thread and delete his and this post.  Somehow he got attached to the wrong thread.**[/SIZE]

---

### Post by jasonrisenburg on 2011-09-02
I know I am going to sound ignorant, but ive been trying to figure out how to edit the xorg file, ca you point me in the right direction? Thank you for your time.

---

### Post by Favux on 2011-09-02
Not at all.  You use *gksudo gedit* on a system file.  _sudo_ to get root permission for a system file and *gksudo* (the graphical version of sudo) to use a graphical program like *gedit*.  Then you just add the path to the file.  So if you wanted to edit the 50-wacom.conf file you would use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```

---

### Post by jasonrisenburg on 2011-09-08
ok this is what is tried. I opened the  command and inserted the 8037 into the driver.

Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WALTOP|WACOM|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|8037|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

---

### Post by Favux on 2011-09-08
Let me make sure I understand what you are telling me.  You added a new line to the hanwang.c source code, something like:
```
	{ 0x8037, "Hanwang Art Master III ????",
	  ART_MASTERIII_PKGLEN_MAX, 0x????, 0x????, 0x3f, 0x7f, 2048 },
```
so it looks something like?
```
static const struct hanwang_features features_array[] = {
	{ 0x8037, "Hanwang Art Master III ????",
	  ART_MASTERIII_PKGLEN_MAX, 0x????, 0x????, 0x3f, 0x7f, 2048 
	{ 0x8528, "Hanwang Art Master III 0906",
	  ART_MASTERIII_PKGLEN_MAX, 0x5757, 0x3692, 0x3f, 0x7f, 2048 },
	{ 0x8529, "Hanwang Art Master III 0604",
	  ART_MASTERIII_PKGLEN_MAX, 0x3d84, 0x2672, 0x3f, 0x7f, 2048 },
	{ 0x852a, "Hanwang Art Master III 1308",
	  ART_MASTERIII_PKGLEN_MAX, 0x7f00, 0x4f60, 0x3f, 0x7f, 2048 },
};
```
And then compiled a new hanwang.ko?

I was going to ask you what the model name was, "Hanwang Art Master III ????".  And also if you could compare the features to the other models.

The 2048 seems likely the pressure levels but I don't know what the other numbers stand for feature-wise.  Especially the two after the model name.  I was hoping we got lucky and your model had the same features as another model and we could use its array without understanding what it is.  Or even better find the model submitted to linux-input (the kernel) with all of that already figured out for us.

---

### Post by jasonrisenburg on 2011-12-07
I have talked to the tablet manufactureor, and as of 12/2/11, there is no support for linux and do not plan on supporting the product.

---

### Post by Favux on 2011-12-07
That's disappointing but not that uncommon a stance by OEM's.  That doesn't mean they won't be supported in linux.  As you can see there already is infrastructure for them.

---

### Post by jasonrisenburg on 2011-12-08
Yeah I know what you mean. I just miss using it and feel almost dirty having to go to windows to use it.. lol. But atleast I can use it right. I wonder if it is closed source? If it is how would we be able to open it?

---

### Post by jasonrisenburg on 2011-12-08
I have found the source code! 
[http://forschung.wi.uni-passau.de/~ond/myweb/hw/hanvon/index.cgi](http://forschung.wi.uni-passau.de/~ond/myweb/hw/hanvon/index.cgi)

Now to try to figure out what to do with it... lol.

---

### Post by jasonrisenburg on 2011-12-08
Call or email to get drivers supported.
Tel: 86-10-82786991

E-mail: [email]info@hanwang.com.cn[/email]

---

### Post by Favux on 2011-12-08
Nice job on finding the source code!

Now you could use the contact info. on that link to ask for help adding your model to the appropriate hanvon.c file.  Like I said it should be relatively simple to add.  And if that's also the same folks submitting the hanvon kernel code then maybe instead ask for help making changes to the kernel code.

It's worth trying to get Hanvon to respond and support Linux so I hope you get folks joining you in that effort.

---

### Post by jasonrisenburg on 2011-12-12
This just came out 
[http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/](http://linux.fjfi.cvut.cz/~taxman/hw/hanvon/)

---

