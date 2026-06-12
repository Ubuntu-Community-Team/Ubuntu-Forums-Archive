---
title: "gongle  huawei E1550 wont work in 10.10"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by gandaran on 2010-10-10
just finished installing 10.10 on both my desktop and netbook, now this mobile dongle E1550 doesn't work, there wasn't any problem using it in 10.04, usb-modeswitch is installed.
I did try it with the live cd and it did work, so whats the thing between the live cd and  the installed Ubuntu?
I have another huawei dongle E169g from the same operator, this one works but on a pre-paid pack, I cant use it all the time so I back to using windows! 
please help I don't want to reinstall 10.04 again.
thanks

---

### Post by alexfish on 2010-10-10
hi

may be udev rules have changed

what happens if re-install usb_modeswitch

also if connection is3g can suggest Sakis3g(usb_modeswitch embeded), it should not be affected by udev rules
even if your not 3g its handy to use for switching such devices

**[*Sakis3G*  - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=Yf-xTLTdO9mX4gb-6MDyBQ&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**



alexfish

---

### Post by gandaran on 2010-10-10
> **alexfish said:**
> hi

may be udev rules have changed

what happens if re-install usb_modeswitch

also if connection is3g can suggest Sakis3g(usb_modeswitch embeded), it should not be affected by udev rules
even if your not 3g its handy to use for switching such devices

**[*Sakis3G*  - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=Yf-xTLTdO9mX4gb-6MDyBQ&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**



alexfish
I did reinstall usb_modeswitch to no avail, this is making me mad, I tried setting it up and rebooting about 10 times and no work so I give up on the desktop and went to the netbook and same thing happened, then I came back to the desktop plugged in the dongle and booted Ubuntu, know what! the d*** thing connected!!!
on the netbook it's still not working.

---

### Post by alexfish on 2010-10-10
going to need some info

when the device is working on desktop

from the terminal

Code:

usb-devices

locate the section which shows your device and post the results

same for netbook

also from system monitor check status of modem-manager and usb_modeswitch and udevd(count) also check status of hald runner with a reverence to -storage finally
udisks daemon

hint hover mouse pointer over target

---

### Post by gandaran on 2010-10-10
> **alexfish said:**
> going to need some info

when the device is working on desktop

from the terminal

Code:

usb-devices

locate the section which shows your device and post the results

same for netbook

also from system monitor check status of modem-manager and usb_modeswitch and udevd(count) also check status of hald runner with a reverence to -storage finally
udisks daemon

hint hover mouse pointer over target
thanks, I will try this tomorrow if I have time, I'm happy now that at least on the desktop I have internet.

---

### Post by alexfish on 2010-10-11
Hi 

it could be the drivers not loading

Try this from the terminal

Code:

[COLOR=Blue]sudo modprobe option[/COLOR]

alexfish

---

### Post by ajeesh cherian on 2010-10-21
Hi,

I am also having the same issue in mounting E1550; thing is that after plugging in the usb modem the windows partitions mounted are also gone.

I have checked /etc/udev/rules.d
Under 70-persistent-cd.rules I could see a rule to 'block' the device mounting is added automatically after Huawai E1550 is plugged in. Below is the entry

# Mass_Storage (pci-0000:00:12.2-usb-0:3:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HUAWEI_Mass_Storage-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"

It also says

# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


I have tried adding another rule, but no go. Does the above scenario rings any bell to anyone? Please help me in configuring my 3G modem....!!

---

### Post by gandaran on 2010-10-21
> **ajeesh cherian said:**
> Hi,

I am also having the same issue in mounting E1550; thing is that after plugging in the usb modem the windows partitions mounted are also gone.

I have checked /etc/udev/rules.d
Under 70-persistent-cd.rules I could see a rule to 'block' the device mounting is added automatically after Huawai E1550 is plugged in. Below is the entry

# Mass_Storage (pci-0000:00:12.2-usb-0:3:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HUAWEI_Mass_Storage-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"

It also says

# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


I have tried adding another rule, but no go. Does the above scenario rings any bell to anyone? Please help me in configuring my 3G modem....!!
check this if it helps
[http://blog.lynxworks.eu/2009/08/huawei-e1550-on-ubuntu/](http://blog.lynxworks.eu/2009/08/huawei-e1550-on-ubuntu/)

---

### Post by ajeesh cherian on 2010-10-21
> **gandaran said:**
> check this if it helps
[http://blog.lynxworks.eu/2009/08/huawei-e1550-on-ubuntu/](http://blog.lynxworks.eu/2009/08/huawei-e1550-on-ubuntu/)

Hi,

Thank you for the reply; but unfortunately that was the same rule I have entered. That work perfect with 10.04 LTS and versions before that. But here the rule I have specified above is blocking the device to be mounted as 'mass storage device'. If it was mounted I could use at least the mobile parter/Idea netsetter application integrated (supports linux) to configure....:(

What can I do....?:confused::confused::confused:
Anybody please help.....

Does this bug ([627672]("https://bugs.launchpad.net/bugs/627672"))  reported in the beta release regarding the "persistence enabled" have any connection with this. Earlier I found the blocking rule under /etc/udev/rules.d/70-persistent-cd.rules.
Also refer [http://www.ubuntu.com/testing/maverick/beta](http://www.ubuntu.com/testing/maverick/beta) check under 'known issues'.

Thanks,
Ajeesh Cherian

---

### Post by ajeesh cherian on 2010-10-21
> **ajeesh cherian said:**
> Hi,

Thank you for the reply; but unfortunately that was the same rule I have entered. That work perfect with 10.04 LTS and versions before that. But here the rule I have specified above is blocking the device to be mounted as 'mass storage device'. If it was mounted I could use at least the mobile parter/Idea netsetter application integrated (supports linux) to configure....:(

What can I do....?:confused::confused::confused:
Anybody please help.....

Does this bug ([627672]("https://bugs.launchpad.net/bugs/627672"))  reported in the beta release regarding the "persistence enabled" have any connection with this. Earlier I found the blocking rule under /etc/udev/rules.d/70-persistent-cd.rules.
Also refer [http://www.ubuntu.com/testing/maverick/beta](http://www.ubuntu.com/testing/maverick/beta) check under 'known issues'.

Thanks,
Ajeesh Cherian
Hi,

I could locate same error reported with the beta release ([625110]("https://bugs.launchpad.net/bugs/625110")) They are recommending to install  udev  version 161+git20100827-1.
How can I install/upgrade it without internet connection when using ubuntu 10.10? Can I download the upgraded version of udev from elsewhere using my Windows machine and later install it on the new Ubuntu?

Am not familiar with that....Please reply with steps...!

Thanks,
Ajeesh Cherian

---

### Post by bill.denbigh on 2010-10-21
I have exactly the same problem with my globe tattoo ZTE 626 modem. This i understand is a problem with modeswitch 1.1.4 that is now included in ubuntu 10.10

A similar problem is reported in:
[https://bugs.launchpad.net/ubuntu/+s...ch/+bug/626568]("https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568")

I have been trying to find help with this here:

[http://ubuntuforums.org/showthread.php?t=1595964](http://ubuntuforums.org/showthread.php?t=1595964)

and:

[http://ubuntuforums.org/showthread.php?t=1594029](http://ubuntuforums.org/showthread.php?t=1594029)

but to date have had no help...

Sorry to not give you a solution, just misery loves company :wink:

---

### Post by ajeesh cherian on 2010-10-23
> **bill.denbigh said:**
> I have exactly the same problem with my globe tattoo ZTE 626 modem. This i understand is a problem with modeswitch 1.1.4 that is now included in ubuntu 10.10

A similar problem is reported in:
[https://bugs.launchpad.net/ubuntu/+s...ch/+bug/626568]("https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568")

I have been trying to find help with this here:

[http://ubuntuforums.org/showthread.php?t=1595964](http://ubuntuforums.org/showthread.php?t=1595964)

and:

[http://ubuntuforums.org/showthread.php?t=1594029](http://ubuntuforums.org/showthread.php?t=1594029)

but to date have had no help...

Sorry to not give you a solution, just misery loves company :wink:

I have connected to an ethernet connection and updated fully...70 packages. Same issue. I have tried installing usb-modeswitch 1.1.3, but system is installing only 1.1.4 version. Then I have removed usb-modeswitch full from the system. Even after that the system does not detect the Huawei E1550 as mass storage device (at least).

If it was detected I could easily configure it using the integrated application....:(

I think this issue has something to do with /etc/udev/rules.d/70-persistent-cd.rules:confused:
[http://ubuntuforums.org/showpost.php?p=10006545&postcount=7](http://ubuntuforums.org/showpost.php?p=10006545&postcount=7)

Anybody plz...plz...help

---

### Post by alexgenaud on 2010-10-26
(me too ... except Huawei e180)

I have a Lenovo x200 running 10.04 which connects using Huawei e180 - I am afraid to upgrade.

Eee PC running 10.10 does not properly mount and hangs while connecting and also

HP Pavilion running 10.10 does not properly mount and hangs while connecting via Huawei e180 mobile broadband usb dongle

---

### Post by ajeesh cherian on 2010-10-27
So till date no solutions????.....
So nobody at the development side of 10.10 does not know anything about it....?? That is shame....!

---

### Post by gandaran on 2010-10-27
> **ajeesh cherian said:**
> So till date no solutions????.....
So nobody at the development side of 10.10 does not know anything about it....?? That is shame....!
file a launchpad bug, would be the best way to get help!
the E1550 is mounted so there must be some way to open the Huawei storage!

---

### Post by ajeesh cherian on 2010-10-28
> **gandaran said:**
> file a launchpad bug, would be the best way to get help!
the E1550 is mounted so there must be some way to open the Huawei storage!


Thank you...!! :) u are saying something different....
We can together get this issue resolved....

How should a file i launchpad bug....plz tell me...

---

### Post by gandaran on 2010-10-28
> **ajeesh cherian said:**
> Thank you...!! :) u are saying something different....
We can together get this issue resolved....

How should a file i launchpad bug....plz tell me...
heres the guide howto
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

or browse the bugs already reported first, maybe someone already has filed one or a very similar one and you can just subscribe to it.
[bugs]("://bugs.launchpad.net/bugs/+bugs?field.searchtext=e1550&orderby=-importance&search=Search&field.status:list=NEW&field.status:list=INCOMPLETE_WITH_RESPONSE&field.status:list=INCOMPLETE_WITHOUT_RESPONSE&field.status:list=CONFIRMED&field.status:list=TRIAGED&field.status:list=INPROGRESS&field.status:list=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

---

### Post by ajeesh cherian on 2010-10-28
Hi,

Thank you all....I will try that..

By the way, I got a new T Mobile USB stick....Its working perfectly with 10.10 now. Its a Huawei E1750
So I am a happy person now..... :)

Cheers  :)
Ajeesh Cherian

---

### Post by alexgenaud on 2010-10-29
Hi Ajeesh,

Have you found a similar or reported a new bug? I've added a comment regarding e180 here.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450805](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450805)

---

### Post by alexgenaud on 2010-10-29
> **ajeesh cherian said:**
> Hi,
By the way, I got a new T Mobile USB stick....Its working perfectly with 10.10 now. Its a Huawei E1750
So I am a happy person now..... :)

It's still worth noting the error for the record:

[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/561821](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/561821)

---

### Post by ajeesh cherian on 2010-10-30
> **ajeesh cherian said:**
> So till date no solutions????.....
So nobody at the development side of 10.10 does not know anything about it....?? That is shame....!


Friends....
I got this issue resolved by using betavine.
Its a good application, using that you can send SMS, track the usage etc

This is what I have done:
1. Uninstalled usb-modeswitch and usb-modeswitch data completely using synaptic.
2. Installed below packages
       python-messaging_0.5.9-1_all.deb (from betavine website)
       usb-modeswitch-data_20100826-1betavine1_all.deb (from betavine website)
       python-gudev_147.2-1_i386.deb (from ubuntu archive - [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-gudev/python-gudev_147.2-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-gudev/python-gudev_147.2-1_i386.deb))
       python-tz_2010b-1_all.deb (from ubuntu archive - [http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-tz/python-tz_2010b-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/p/python-tz/python-tz_2010b-1_all.deb))
       wader-core_0.5.5-1_all.deb (from betavine website)
       wmctrl_1.07-6_i386.deb (from ubuntu archive - [http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wmctrl/wmctrl_1.07-6_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/w/wmctrl/wmctrl_1.07-6_i386.deb))
       bcm_2.99.12-1_all.deb (from betavine website)

After that restarted the system, then connected the usb modem. Then opened betavine connection manager from Applications > Internet
It automatically detected the device, just entered my BSNL 3G APN, clicked connect and thats it....  :)

Below is the [weblink]("https://forge.betavine.net/frs/?group_id=76") from which you may download betavine packages
[https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76)

Refer betavine [blog]("http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812942915f01294cd0e6e322bc") for more details.
You may also get this application for Mandriva or SuSe or Fedora or Moblin from [here]("http://www.betavine.net/bvportal/resources/datacards/os/")

Hope that helped....:guitar:


Cheers :)
Ajeesh Cherian

---

### Post by ramakrishna91 on 2011-01-08
hie.......i am a NEWBIE to linux......just finished installing ubuntu on my lappy......
   i dont know how to install  my "huawei e1550 idea net setter" on ubuntu.....
  in windows as soon as i plugin the device the driver automatically installs.....
  PLEASE help me to do so in ubuntu......

---

### Post by ajeesh cherian on 2011-01-08
> **ramakrishna91 said:**
> hie.......i am a NEWBIE to linux......just finished installing ubuntu on my lappy......
   i dont know how to install  my "huawei e1550 idea net setter" on ubuntu.....
  in windows as soon as i plugin the device the driver automatically installs.....
  PLEASE help me to do so in ubuntu......


Hi Ram,

Netsetter already have a Linux folder in it. Please explore it. There is a readme file, follow the instructions to install the "Mobile Partner" application.
After installing that, ubuntu will automatically detect the device and will launch the application.

Let me know if you have any more doubts.
Netsetter is already locked, you can use Idea SIM only with that device. You can get it  unlocked and use BSNL 3G SIM.

---

### Post by SivArt on 2011-01-29
I am having a problem with my dongle, I have a Huawei E1550, if I plug it in, ubuntu immediately detects it, if I go to Network Manager and select it, it asks me for the PIN, but just after that, Ubuntu locks up.

Any help will be really appreciated.

SivArt

---

