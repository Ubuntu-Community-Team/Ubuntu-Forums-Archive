---
title: "How do I get my scanner to wok?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Irish1 on 2009-04-25
How do I get my scanner to work?  Ubuntu knows that I have a scanner and even knows what kind it is, but won't access it.  Any suggestions?

---

### Post by cwsnyder on 2009-04-25
Is your scanner listed on the [www.sane-project.org](www.sane-project.org) compatibility list?  Are you using a Windows driver?  How do you know Ubuntu 'knows what kind' your scanner is?  Just because it shows with cat /proc/bus/usb/devices does not mean that Ubuntu has a proper driver for the scanner.

---

### Post by Irish1 on 2009-04-25
I know Ubuntu recognizes the scanner because the terminal message says the exact the of scanner, but hen XSane does nothing but give me an error message.

---

### Post by wizard10000 on 2009-04-25
> **Irish1 said:**
> I know Ubuntu recognizes the scanner because the terminal message says the exact the of scanner, but hen XSane does nothing but give me an error message.

Can we keep the topic to one thread, please?  :)

I don't think you have a SCSI scanner.  I think the guy who told you you needed a SCSI driver had no idea what he was talking about.

---

### Post by Sef on 2009-04-25
What scanner do you have?

---

### Post by Irish1 on 2009-04-25
I have a Lexmark X-73 printer/scanner.  The printer works fine.

---

### Post by Ruhani04 on 2009-04-25
I have a similar problem. I just installed jaunty and my scanner did not work (brother mfc 240c). It has to do with access permissions which used to be easily changed in 8.10. In 9.04 that permissions file does not exist anymore. My work around is to run "sudo xsane".

---

### Post by SunnyRabbiera on 2009-04-25
> **Irish1 said:**
> I have a Lexmark X-73 printer/scanner.  The printer works fine.

Lexmark, thats your problem...
Lexmarks have crap support for linux.
Trade it in for a HP

---

### Post by Kellemora on 2009-04-26
Hope SR don't mind if I STRONGLY Disagree with him?

NOTHING we have here made by HP home division works right, never has and never will.  Their commercial grade is a different class of product and most of the commercial stuff is Unix/Linux, if you can afford the exorbitant price tags that is.

HP does NOT even write drivers for an HP branded computer with an HP scanner of the same vintage running the DOZE..........
And they WON'T give Xsane the data necessary to write a LINUX driver for them either!

We ran 12 low end Lexmark printers about 3 hours per day each without a single breakdown or repair issue over a 4 year span.

However, although I don't own any yet, I've been looking at Epson because they DO provide Xsane with the necessary info to write drivers for Linux.
Don't know if they are any good though yet!

I'm in the market for new scanners myself, but holding off until an OEM supports Linux and whoever that is, they will get my business!
Even if it's the worst piece of junk one could imagine, I will stand behind them 100% for supporting Linux!

TTUL
Gary

---

### Post by anewguy on 2009-05-10
the udev rules have changed in 9.04 (again, undocumented).  I will assume your printer/scanner is a usb device.  Post the output of sudo lsusb back here and I think we can fix this for you.  I have had the same problem with some special usb cameras I have and have had to fight undocumented changes in udev about every time they change major release.  I have mine working in 9.04 and I think we can problably set something up for you as well.

As a note, as mentioned earlier in this post, the device is accessable if the app is run as root (or su).  this is the primary indication that the rules in udev are messing this up - in particular, some usb devices get mounted via udev with root as the owner and no one else can access the device (it will show in lsusb, but your app can't access it unless su or root).

What was required for me was as follows:

- the udev rules files moved from /etc to /lib in 9.04, so the path to the rules is now /lib/udev/rules.d

- as su or root, open a new file in an editor.  In this file add a line (or lines if multiple devices) as follows:

== first syntax type  ==

output from lsusb shows vendor:productid such as 01bc:0405

add this line to the new file:

SUBSYSTEMS=="usb" ATTRS{idVendor}=="01bc" ATTRS{idProduct}=="0405" MODE:="0666"

Where 01bc should be changed to what ever is before the ":" from lsusb, and 0405 should be changed to what ever is after the ":" from lsusb.


== second syntax type ==

output from lsusb shows a vendor name and a product name, such as in My Device, Inc. Model4.

add this line to the new file:

SUBSYSTEMS=="usb" ATTRS{manufacturer}=="My Device, Inc." ATTRS{product}=="Model4" MODE:="0666"


After adding the needed line to this new file, save it as:

/lib/udev/rules.d/10-local-permissions.rules

Then exit the editor.  You can either reboot at this time or restart udev via:  sudo /etc/init.d/udev --restart  (I think that's the syntax).

Since both versions made the mode "0666", the device should be available to anyone now - try the app as a regular user instead of as su or root - it should work.

Dave :)

---

### Post by maxbur on 2009-05-18
Dave,
Your simple, if not downright elegant, solution had my scanner up and running again as fast as I could type it out and reboot. Thank you.

(As the scanner isn't used frequently, I'm unsure if the permissions problem arose from a recent upgrade to Jaunty 9.04, or from powering down the scanner itself.)

---

### Post by alpeter on 2009-05-21
> **Sef said:**
> What scanner do you have?
use open office with presentations xsane will no recognize and iam a beginner  good luck

---

### Post by alpeter on 2009-05-21
> **Irish1 said:**
> I know Ubuntu recognizes the scanner because the terminal message says the exact the of scanner, but hen XSane does nothing but give me an error message.
if you have a hp scanner hp's software was no good anyway use open office under presentation xsane will not work for me with my allinone 1210 but open office will  gdluk

---

### Post by anewguy on 2009-05-21
> **maxbur said:**
> Dave,
Your simple, if not downright elegant, solution had my scanner up and running again as fast as I could type it out and reboot. Thank you.

(As the scanner isn't used frequently, I'm unsure if the permissions problem arose from a recent upgrade to Jaunty 9.04, or from powering down the scanner itself.)

You're welcome.  It's one of those undocumented things, including in the release notes, that changed.  I normally wouldn't be familiar with this but I have a couple of "special" usb cameras that have required messing around in the permissions since 7.10.

I just wish they would document this more!

Dave :)

---

### Post by anewguy on 2009-05-21
> **alpeter said:**
> if you have a hp scanner hp's software was no good anyway use open office under presentation xsane will not work for me with my allinone 1210 but open office will  gdluk


Sorry to hear about your experience with your HP combo.  Did you try what I suggested to see if it would work for you in xsane?  I know many more of us that have HP printers and HP scanners that haven't ever had a problem, so I was sorry to hear you did.  HP support for Linux is very good - that has a lot to do with their commercial product lines.

Dave :)

---

### Post by vayira on 2009-06-19
> **anewguy said:**
> What was required for me was as follows:

- the udev rules files moved from /etc to /lib in 9.04, so the path to the rules is now /lib/udev/rules.d

- as su or root, open a new file in an editor.  In this file add a line (or lines if multiple devices) as follows:

== first syntax type  ==

output from lsusb shows vendor: productid such as 01bc:0405

add this line to the new file:

SUBSYSTEMS=="usb" ATTRS{idVendor}=="01bc" ATTRS{idProduct}=="0405" MODE:="0666"

Where 01bc should be changed to what ever is before the ":" from lsusb, and 0405 should be changed to what ever is after the ":" from lsusb.


== second syntax type ==

output from lsusb shows a vendor name and a product name, such as in My Device, Inc. Model4.

add this line to the new file:

SUBSYSTEMS=="usb" ATTRS{manufacturer}=="My Device, Inc." ATTRS{product}=="Model4" MODE:="0666"


After adding the needed line to this new file, save it as:

/lib/udev/rules.d/10-local-permissions.rules

Then exit the editor.  You can either reboot at this time or restart udev via:  sudo /etc/init.d/udev --restart  (I think that's the syntax).

Since both versions made the mode "0666", the device should be available to anyone now - try the app as a regular user instead of as su or root - it should work.

Dave :)

Just commenting to help other users.

The above enabled me to use xsane as a normal user in 9.04 Jaunty 64bit with a canon N670u. 

Only error now is files permissions when I close xsane (presumably to save configs)... but I can live with that.

---

### Post by francois_montandon on 2009-07-02
Hello,

Have an Epson Perfection V 10... After approx. 4 hours trying to install, I surrender.

Have tried, Epson Avasys site, Sane projetc, etc... Absolutely nothing works, "Image Scan" can never detect the device...

... New to Ubuntu, really hard...

Read somewhere that Linux will be succesful when it will get a distribution that my mum can use... We are very far from that... she already calls me once a week with MS Windows... With this, I would spend the whole day on the phone.

Thx for helping.

---

### Post by theozzlives on 2009-07-02
I have an Epson CX-8400 all-in-one that I couldn't get the scanner to work on in 8.10. I had to use an old Mustek I had laying around. When I went to Jaunty, IT WORKED! Maybe just 8.10.

---

