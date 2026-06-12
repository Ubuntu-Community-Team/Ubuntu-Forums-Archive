---
title: "Scroll (wheel) speed, mouse acceleration, threshold, sensivity"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Seregwethrin on 2009-06-05
Hello;

In Windows, if you move your mouse faster than your mouse's acceleration increases. For example you may move mouse 10cm to move pointer most left of screen to most right by slowly, but if you move fastly, you could take the same distance with moving 3cm. I want to do this in my Ubuntu 9.04, but I couldn't find a setting.

Sensivity: I checked the help file but I didn't understand. Can somebody give an example for what this setting does?

Threshold: I didn't understand same as sensivity.

Also I want to increase my mouse's scrolling speed (wheel speed). Is there any setting or any way to do this?

Thanks.

---

### Post by Seregwethrin on 2009-06-06
Still waiting for a solutions... :(

---

### Post by mgmiller on 2009-06-06
Go to  System > Preferences > Mouse

On the general tab, the slider labeled "Acceleration" next to Pointer speed should do what you want.  I tried moving mine up and I can fling my cursor all over the screen with a quick flick.

These sliders are somewhat interdependent, so only move one of them at a time and see what happens.  The changes take place instantly with the window still open, so you don't have to click OK or anything.

As far as setting the scroll wheel, I am not aware of any system wide setting for that.  It may be possible to change the setting in firefox.
Run Firefox and in the address bar type
```
about:config
```In the Filter field at the top, put in:
```
mousewheel.withnokey
```My default setting shows .numlines as 1 and .sysnumlines as true.

This gives me the default behavior of  3 line scroll with each click of my mouse wheel.

Double click the line that ends in .sysnumlines and the value will change from true to false.

Next, double click the line that ends in .numlines and put in the number of lines you want the page to scroll with each click of the mouse wheel.

The changes take place immediately without having to restart Firefox.

Edit:

I have edited the above for better clarity.

---

### Post by Seregwethrin on 2009-06-06
It's what I'm asking for, It's actually the speed of pointer. I want my pointer runs faster when I run mouse faster but not proportional. I want pointer more faster when mouse moves faster.... I want it to adjust itself by the speed of mouse.

---

### Post by mgmiller on 2009-06-06
I have edited the instructions for the mouse wheel scrolling for better clarity.

---

### Post by Seregwethrin on 2009-06-06
I've already done it mate but it just works for firefox, I want scrolling faster at other programs too :)

---

### Post by mgmiller on 2009-06-07
This is a known issue.  There used to be a fix for this by editing xorg.conf, but all the mouse hardware config is now done by hal and is supposed to be automatic.  There will hopefully be a change in the upcoming gnome that will allow us to adjust more of the mouse features including the scroll wheel, but for now, I don't think it can be done.     ](*,)

---

### Post by Seregwethrin on 2009-06-07
Thanks for explanation mate, I hope new gnome will support as you said.

---

### Post by jastonas on 2009-11-14
Is there still no fix for the scroll speed? It is making my ubuntu experience really bad, almost unbearable, having my wheel scrolling half a page even with a gentle touch

---

### Post by mgmiller on 2009-11-14
Here are settings within firefox itself that affect scroll wheel speed.  Only for Firefox though, not the rest of Gnome.

How to change the number of lines that scroll in Firefox with each click of the mousewheel.

  Run Firefox and in the address bar type
Code:
```
about:config
```

In the Filter field at the top, put in:
Code:
```
mousewheel.withnokey
```

My default setting shows .numlines as 1 and .sysnumlines as true.

This gives me the default behavior of 3 line scroll with each click of my mouse wheel.

Double click the line that ends in .sysnumlines and the value will change from true to false.

Next, double click the line that ends in .numlines and put in the number of lines you want the page to scroll with each click of the mouse wheel.

The changes take place immediately without having to restart Firefox.

---

### Post by Seregwethrin on 2009-11-14
It's just a solution for Firefox, not all programs...

---

### Post by jastonas on 2009-11-14
Yeah I did that, helped a bit but it is still annoying enough. This problem and mostly my wireless adapter not working have made me use win 7 :/

---

### Post by jotiho on 2009-11-15
I have a similar problem in xubuntu 9.10.  I want to speed up my mouse response (ie, increase the screen distance travelled for a given mouse displacement), but there does not seem to be a speed setting among the mouse options: only acceleration and sensitivity.  Is there a way around this?  It's very frustrating to work with such a low screen/mouse ratio.

Thanks for any suggestions.

---

### Post by jlhaslip on 2009-11-24
in the about:config, adjust the settings for mousewheel.*withshiftkey*.numlines to a different setting and you will then have a faster scrolling when you add the shift with your scrolling. :P
that will allow you a really fast scroll for those times you need it.

---

### Post by ledomira on 2010-03-04
This won't fix everything, like the scroll wheel speed, but to change your mouse sensitivity, the best solution I've found is to use xset.  If it's not already on your system, you'll need to download it from the repositories.  Then, open up a terminal and type:

xset m 6 2

Xset is a program that sets all sorts of stuff.  m refers to the mouse and 6 2 is the acceleration and threshold.  Feel free to play around with the numbers to get what you want.  A lot of people like 5 1.

As for the wheel problem, I use a trackball that doesn't have a wheel, so I use wheel emulation.  I hold down the middle mouse button and the move the trackball and it emulates the wheel.  I type this in the console to do that:

xinput set-int-prop "PS/2 Logitech TrackMan" "Evdev Wheel Emulation Axes" 8 6 7 4 5 
xinput set-int-prop "PS/2 Logitech TrackMan" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "PS/2 Logitech TrackMan" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "PS/2 Logitech TrackMan" "Evdev Wheel Emulation Inertia" 16 5

That probably won't help you though.  You would replace "PS/2 Logitech TrackMan" with whatever your mouse is called.  You find that out by typing xinput --list --short.  You're devices will show up so you can see what the system calls it.

I wonder if changing the Evdev Wheel Emulation Inertia would affect the actual wheel.  It definitely affects it when it's emulated (higher numbers cause more friction, lower numbers cause less)  The first 8 of the numbers in the first 3 lines are necessary, not sure for what.  Same with the 16 in the fourth line.

At the very least, xset m 6 2 should help.

The next problem is getting it to start every time your computer boots.  I ended up having to go to my home folder, viewing hidden files, opening ./config/autostart and creating a .desktop file that would run xset every time I booted.  I found other .desktop files and edited them to figure it out.  Ultimately though, I couldn't get programs to start consistantly and ended up moving to Crunchbang linux, which is still based on Ubuntu, but uses Openbox as the window manager instead of Gnome, so it's a lot faster.  It uses an autostart.sh script file that's easy to add stuff to, but it requires more work overall because it won't do stuff like add menu entries for you when you install a program.

---

### Post by jastonas on 2010-03-04
My experience with my mouse scroll speed:
Working perfectly fine under windows 7 and ubuntu. But if i log in windows and then go to ubuntu (even with a shutdown) the speed freaks out and scrolls 10 times instead of 2-3... all i need to do is **unplug and plug again the usb adaptor** for my wireless keyboard-mouse.

---

### Post by ubunwhat? on 2010-07-05
Thanks Jastona! My mouse wheel was scrolling about a page and a half instead of 2-3 lines! That was quite annoying. Your work around worked perfectly.

---

### Post by jastonas on 2010-07-06
> **ubunwhat? said:**
> Thanks Jastona! My mouse wheel was scrolling about a page and a half instead of 2-3 lines! That was quite annoying. Your work around worked perfectly.

"workaround"

That one required real hacking skills :D

---

### Post by michaelzap on 2010-07-07
> **jastonas said:**
> "workaround"

That one required real hacking skills :D

I never would've thought of trying this, and it worked for me with my wireless Microsoft mouse also. I didn't make the connection between having booted into Windows for the first time in months and my mouse scrolling way too fast (I suspected an update at first, but there were none that seemed related). THANKS for the info!

---

### Post by Nowaker on 2011-01-28
```

sudo chmod +r /dev/input/event2; xwheeldoubler /dev/input/event2 3 &
```

/dev/input/event2 - your mouse
3 - how many times faster

AFAIR, libxtst6 package is needed (libxtst-dev for compiling).
Compiled version for amd64 in attachment. The source code below.

```

gcc -lXtst xwheeldoubler.c

```

```

#include <stdio.h>
#include <stdlib.h>
#include <linux/input.h>
#include <sys/types.h>
#include <fcntl.h>
#include <X11/extensions/XTest.h>

Display *dpy;
int file;

void cleanup()
{
	if(file) {
		close(file);
	}
	if(dpy) {
		XCloseDisplay(dpy); 
	}
}

int main(int argc, const char** argv)
{
	if(argc < 3) {
		printf("Usage: %s <event_device> <how_many_times_faster>\n", argv[0]);
		return 1;
	}

	atexit(cleanup);
	if((file = open(argv[1], O_RDONLY)) <= 0) {
		perror("open");
		return 2;
	}
	struct input_event event;
	if ((dpy = XOpenDisplay(NULL)) == NULL) {
		fprintf(stderr, "Can't open display\n"); 
		return 3;
	}

	int times = atoi(argv[2]) - 1;
	size_t n;
	while((n = read(file, &event, sizeof(struct input_event)))>0) {
		if(event.type == 0x02 && event.code == 0x08) {
			if(event.value > 0) {
				int i = 0;
				for (; i < times; i++) {
					XTestFakeButtonEvent(dpy, 4, True, CurrentTime);
					XTestFakeButtonEvent(dpy, 4, False, CurrentTime);
				}
			} else {
				int i = 0;
				for (; i < times; i++) {
					XTestFakeButtonEvent(dpy, 5, True, CurrentTime);
					XTestFakeButtonEvent(dpy, 5, False, CurrentTime);
				}
			}
			XFlush(dpy);
		}
	}
	return 0;
}

```

Known bugs: 100% cpu after pulling in/out any USB device. Feel free to fix it. ;-]

Source code licensed under GNU GPL v3.

---

### Post by mlarsen23 on 2011-03-16
Can you give any explanation on how to turn that code you posted into a working program?

---

### Post by synchro505 on 2011-04-11
+1

It would be great to learn a more about how this works for noobs like me.

Of course, it would be even better if the Mouse Preferences control panel had a scroll adjustment slider!
;)

---

### Post by The Chef on 2011-05-13
Here is a fantastic simple solution that worked for me:

See: [http://ubuntuforums.org/showthread.p...24#post8583324](http://ubuntuforums.org/showthread.p...24#post8583324)

---

### Post by The Chef on 2011-05-13
I had same problem with all the wireless mice I used in all application windows, not just Firefox.  The scrolling was hypersensitive.  The Firefox settings did nothing, and would not have been a global solution.

BUT this fantastically simple solution worked for me:

[http://ubuntuforums.org/showthread.p...24#post8583324](http://ubuntuforums.org/showthread.p...24#post8583324)

Basically, when the PC is running, unplug the wireless USB dongle count to 3 and plug it back in.  All fixed.  Still no way to micro adjust, but I get a sensible wheel sensitivity after doing this.

---

### Post by blitzter47 on 2011-06-04
> **The Chef said:**
> I had same problem with all the wireless mice I used in all application windows, not just Firefox.  The scrolling was hypersensitive.  The Firefox settings did nothing, and would not have been a global solution.

BUT this fantastically simple solution worked for me:

[http://ubuntuforums.org/showthread.p...24#post8583324](http://ubuntuforums.org/showthread.p...24#post8583324)

Basically, when the PC is running, unplug the wireless USB dongle count to 3 and plug it back in.  All fixed.  Still no way to micro adjust, but I get a sensible wheel sensitivity after doing this.

The link is incomplete/mistyped

---

### Post by The Chef on 2011-06-06
Hi. Yeah, seems to have disappeared.  It was a huge thread with about 175 pages.  Moved maybe?  Anyhow, the problem seems to arise when you dual boot into Windows, and Windows leaves the mouse wheel sensitivity extremely high, even after a cold boot into Ubuntu.  Which, I know, sounds pretty weird.  Anyway, the fix that is shown in a number of threads is to simply unplug the USB wireless dongle and plug it back in when Ubuntu is running. Then the mouse wheel is back to a normal 3 lines per click behaviour, at least until the next time you boot into Windows.  Sorry about the broken link.:confused:

---

### Post by junix on 2011-07-01
Yes, you are correct!

I have the same crazy problem and the solution is unplug the usb and plug again.

That's it!

Best regards,

Junix

---

### Post by Tekno.Statik on 2011-07-24
Vote for a solution here, I'm still trying to have developers do something about it for MONTHS.

I've tried getting "Gestikk" but failed at making it work, and I feel I should not have to fill my mind with such garbage just to use it once for scrolling.

Vote here:

[[IMG]http://brainstorm.ubuntu.com/idea/27631/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/27631/)

Add your vote if you want a GLOBAL (Not just Firefox) solution to the scrolling which does not require as many CODES and applications in Terminal (Sure, codes are easy to paste, except when they fail for x or y reason).

Something like this should be far more automatic.

---

### Post by Danstroem on 2011-09-01
Hey Nowaker,

thanks for your wonderful program! It works like a charm, if you want to accelerate the mouse wheel!

Here is what I did to get your program killed and executed automatically, when the mouse is plugged in. Create the file /etc/udev/rules.d/xwheeldoubler as root and paste this content:
```
SUBSYSTEM=="input", ATTRS{idVendor}=="045e", ATTRS{idProduct}=="0040", RUN+="/home/YOUR-NAME/bin/xwheeldoubler.sh /dev/input/%k &"
```Change the vendor id and product id appropriately to your mouse. Get the info with

```
lsusb

```while the mouse is attached.

Create the file /home/YOUR-NAME/bin/xwheeldoubler.sh, chmod 755 and paste the following:
```
#!/bin/bash

# Desktop user
USERNAME="YOUR-NAME"

# Display to operate on
export DISPLAY=":0.0"

if [ "$1" == "/dev/input/event9" ]; then
  if [ -c "$1" ]; then
    if [ -r "/var/run/gdm" ]; then
      export XAUTHORITY="`ls /var/run/gdm/*/database|grep auth-for-$USERNAME-`"
    fi
    /home/$USERNAME/bin/xwheeldoubler $1 5 &
  else
    killall xwheeldoubler;
  fi
fi
```Remember to change YOUR-NAME to your desktop username and to change  event9. The right eventX for your mouse can be seen in /dev/input/by-id or /dev/input/by-path. Copy the xwheeldoubler binary to the folder /home/YOUR-NAME/bin. The multiply factor here is 5. Change it, if you want. The XAUTHORITY variable is necessary for xwheeldoubler to talk to your X server.

I like Linux :-)

By the way: if you have a notebook with touchpad and you want to accelerate this, too, you can put the following in /etc/X11/xorg.conf:
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "synaptics"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    # accelerate vertical scrolling (default: 25)
    Option         "VertScrollDelta" "6"
EndSection
```It depends on your xorg.conf, if you have to modify you existing InputDevice section, or if you have to add a new one. For Firefox, you can also change the wheel sensitivity, by typing about:config as address and look for the key mousewheel.withnokey.sysnumlines. Set it to false and modify mousewheel.withnokey.numlines. I changed it from 6 to 3, as otherwise Firefox would scroll too fast.


> **Nowaker said:**
> ```

sudo chmod +r /dev/input/event2; xwheeldoubler /dev/input/event2 3 &
```/dev/input/event2 - your mouse
3 - how many times faster

AFAIR, libxtst6 package is needed (libxtst-dev for compiling).
Compiled version for amd64 in attachment. The source code below.

```

gcc -lXtst xwheeldoubler.c

``````

#include <stdio.h>
#include <stdlib.h>
#include <linux/input.h>
#include <sys/types.h>
#include <fcntl.h>
#include <X11/extensions/XTest.h>

Display *dpy;
int file;

void cleanup()
{
    if(file) {
        close(file);
    }
    if(dpy) {
        XCloseDisplay(dpy); 
    }
}

int main(int argc, const char** argv)
{
    if(argc < 3) {
        printf("Usage: %s <event_device> <how_many_times_faster>\n", argv[0]);
        return 1;
    }

    atexit(cleanup);
    if((file = open(argv[1], O_RDONLY)) <= 0) {
        perror("open");
        return 2;
    }
    struct input_event event;
    if ((dpy = XOpenDisplay(NULL)) == NULL) {
        fprintf(stderr, "Can't open display\n"); 
        return 3;
    }

    int times = atoi(argv[2]) - 1;
    size_t n;
    while((n = read(file, &event, sizeof(struct input_event)))>0) {
        if(event.type == 0x02 && event.code == 0x08) {
            if(event.value > 0) {
                int i = 0;
                for (; i < times; i++) {
                    XTestFakeButtonEvent(dpy, 4, True, CurrentTime);
                    XTestFakeButtonEvent(dpy, 4, False, CurrentTime);
                }
            } else {
                int i = 0;
                for (; i < times; i++) {
                    XTestFakeButtonEvent(dpy, 5, True, CurrentTime);
                    XTestFakeButtonEvent(dpy, 5, False, CurrentTime);
                }
            }
            XFlush(dpy);
        }
    }
    return 0;
}

```Known bugs: 100% cpu after pulling in/out any USB device. Feel free to fix it. ;-]

Source code licensed under GNU GPL v3.

---

### Post by Seregwethrin on 2011-09-09
Hi Danstroem

I actually can't understand how to find eventX?
Please have a look at this

```

$ ls /dev/input
by-id    event0  event2  event4  js0   mouse0
by-path  event1  event3  event5  mice  mouse1

$ ls /dev/input/by-id
usb-073a_2230-event-mouse
usb-073a_2230-mouse
usb-Logitech_USB_Receiver-event-kbd
usb-Logitech_USB_Receiver-event-mouse
usb-Logitech_USB_Receiver-if01-event-mouse
usb-Logitech_USB_Receiver-if01-mouse
usb-Logitech_USB_Receiver-mouse
```

Now what is eventId for my mouse?
*Note: My keyboard and mouse have one receiver.*

---

### Post by Danstroem on 2011-09-09
try```
ls -l /dev/input/by-id
```It will show you the symlinks to eventX. If it's still not clear, you can just try the eventX's one after the other and try, which one is correct. Nothing will get destroyed ;-)

---

### Post by Seregwethrin on 2011-09-09
```
$ ls -l /dev/input/by-id/
total 0
lrwxrwxrwx 1 root root 9 2011-09-09 14:25 usb-073a_2230-event-mouse -> ../event4
lrwxrwxrwx 1 root root 6 2011-09-09 14:25 usb-073a_2230-mouse -> ../js0
lrwxrwxrwx 1 root root 9 2011-09-09 14:25 usb-Logitech_USB_Receiver-event-kbd -> ../event2
lrwxrwxrwx 1 root root 9 2011-09-09 14:25 usb-Logitech_USB_Receiver-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2011-09-09 14:25 usb-Logitech_USB_Receiver-if01-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2011-09-09 14:25 usb-Logitech_USB_Receiver-if01-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 2011-09-09 14:25 usb-Logitech_USB_Receiver-mouse -> ../mouse0
```

I tried putting event3 event4 and mouse0 into ~/bin/xwheeldoubler.sh with also changing my username. Also I use always first display (left most upper one)

With executing .sh script there's no error message, no success message, and no running process shown with "ps aux | grep xwheel"

Also it didn't work :(

My ~/bin/xwheeldoubler.sh file
```
#!/bin/bash

# Desktop user
USERNAME="Seregwethrin"

# Display to operate on
export DISPLAY=":0.0"

if [ "$1" == "/dev/input/event3" ]; then
  if [ -c "$1" ]; then
    if [ -r "/var/run/gdm" ]; then
      export XAUTHORITY="`ls /var/run/gdm/*/database|grep auth-for-$USERNAME-`"
    fi
    /home/$USERNAME/bin/xwheeldoubler $1 5 &
  else
    killall xwheeldoubler;
  fi
fi
```

---

### Post by Danstroem on 2011-09-09
try to run```
sudo /home/Seregwethrin/bin/xwheeldoubler /dev/input/eventX 5
```from bash. event3 or event4 should be correct. The binary should start without messages. Try, if the wheel is accelerated. You can abort xwheeldoubler with hitting CTRL+C. Try event3 and event4. Are you sure, that your username is written with an uppercase 'S'?

---

### Post by Seregwethrin on 2011-09-09
Nope... Doesn't work.

Username is correct, no problem with it.

I just can't see xwheeldoubler in ps aux. I see one time which I wrote ps aux very fast, it showed and I typed ps aux again and then it was gone. Also I tried with sudo too and I tried running with current user both.

I also changed /home/$USERNAME/bin/xwheeldoubler $1 15 & to /home/$USERNAME/bin/xwheeldoubler.sh $1 15 &
(Added .sh extensions to at the end of the file name)

Still same exact wheel speed...

Also when I run the sh file at terminal, the terminal exactly goes to new command line. Which means I never had to press CTRL+C.

---

### Post by Danstroem on 2011-09-09
I couldn't get it from your post. You tried the binary from bash exactly as typed below (without .sh)?
```
 sudo /home/Seregwethrin/bin/xwheeldoubler /dev/input/event3 5
``` and
```
 sudo /home/Seregwethrin/bin/xwheeldoubler /dev/input/event4 5
```and it immediately returned without any message? Could you do an ```
echo $?
``` directly after you tried xwheeldoubler (not the script, but the binary)? Don't run anything else in between, even not ps aux. $? prints the error code from the last command, in this case the binary. The script xwheeldoubler.sh will indeed return immediately, because it runs the binary xwheeldoubler in the background and returns.

edit: when you change xwheeldoubler to xwheeldoubler.sh in the script, this will not work, because the script would call itself and never the binary we need.

---

### Post by Danstroem on 2011-09-12
Hey Seregwethrin, is there any progress yet?

---

### Post by Seregwethrin on 2011-09-12
wait... missed something :)

---

### Post by Seregwethrin on 2011-09-12
Nope, didn't miss anything :(

I mean there's no ~/bin/xwheeldoubler binary? only ~/bin/xwheeldoubler.sh

So running this as you suggested:
```
 sudo /home/Seregwethrin/bin/xwheeldoubler /dev/input/event3 5
```
just gives "Command not found" error on the command line.

Where does the binary file come from?

---

### Post by Danstroem on 2011-09-13
From [Post #20 from Nowaker]("http://ubuntuforums.org/showpost.php?p=10406312&postcount=20"). He wrote the binary xwheeldoubler, which does the doubling or multiplying. If you run the binary directly from your shell as root, it will accelerate your mousewheel. This is the line in post #35. If you only occasionally want to accelerate your mousewheel, this will do it.

Because I have a notebook, I wanted this binary to get called automatically, when the mouse gets plugged in. This is the purpose of the micro-howto in post #29. udev will do the trick, but the xwheeldoubler binary has to be wrapped into a shellscript (xwheeldoubler**.sh**). udev calls the scipt automatically, when the mouse gets connected or disconnected, because we told him with putting a file into /etc/udev/rules.d. udev calls the script. The script looks, if the mouse was plugged in or out and starts or kills the xwheeldoubler binary. Killing is important, because the binary will produce 100% CPU usage, when the mouse gets disconnected.

If you have a 64 bit Ubuntu, you can take the attached binary from Post #20. If you have a 32 bit system, you will need to compile the binary. Look into Post #20 for how to do that. Remember to do a chmod 755 on the binary. If you have further questions, just write them down ;-)

---

### Post by Seregwethrin on 2011-09-20
Thank you Danstroem very very thank you :)

You solved the main problem why I can't use Linux more often.

It works like a charm!

And sorry again I couldn't see the binary
And sorry for my late replies, I had an exam :)

---

### Post by talcou on 2011-09-23
Excellent, it works, great thanks!!
Had to use /dev/input/event4 to make it work.

Ciao.

---

### Post by Seregwethrin on 2011-10-01
I have a little problem now.

The /dev/input/eventX files are changing at startup, generally the mouse may be event3 or event4. I guess because there's many usb devices plugged into my computer.

Is there any way to make the xwheeldoubler.sh file more consistent for my situation?

---

### Post by Danstroem on 2011-10-02
Wow, I thought this was udev's right to exist: to name the devices consistent and reproducible...

Maybe this works for you:

Open xwheeldoubler.sh, find the line
```
if [ "$1" == "/dev/input/eventX" ]; then
```and replace it with
```
if [ "`echo $1 | grep /dev/input/event`" != "" ]; then
```Note, that there is no number after "event". This makes sure that all eventX get caught for your mouse. Whether it is input3 or input4 or whatever. ;-) Please post here, if it works or not!

---

### Post by shuttleworthwannabe on 2012-02-04
[This]("http://ubuntuforums.org/showpost.php?p=10503301&postcount=2") neat solution fixed it for me.

---

