---
title: "Well... I'm stuck"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by Globox on 2007-06-25
Hey everyone, I just installed the latest dist of Ubuntu desktop (7.04) on my Dell Latitude D600. I followed a guide ([http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)) but have had no luck. I read a lot of the posts in this guide, and people seemed to mention NDISwrapper, though I'm not sure what it is or how to use it--and judging by the general negative comments on it I'm not sure that I'd want to.

Anyway, when I run the iwconfig command I get this:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So it says I have a Broadcom 4306, which is supposedly supported with fwcutter installed, according to this guide. But I haven't been able to get it working. I followed the instructions of the guide very carefully, and I also found another guide that said not to extract the files to /lib/firmware/ but instead to /lib/firmware/<dist-version> (which, in my case, would be: /lib/firmware/2.6.20-16-generic/) but neither of these methods work.

I'm stuck, and I need help, is there anything I can/should do? Am I missing something?

I think it's important to note that my wired card works perfectly. Isn't it the same chipset as the wireless card?

I'm not very well-rounded in Linux, though I can find my way around Unbutu *OK*. Detailed responses are appreciated.

---

### Post by jimbob on 2007-06-25
I followed the first post in this thread and it worked perfectly for me:

  [http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Globox on 2007-06-25
> **jimbob said:**
> I followed the first post in this thread and it worked perfectly for me:

  [http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...
Well, I attempted that guide and when it got to the installation of the Windows driver step:
> sudo ndiswrapper -i /location_of_wireless_driver/bcmwl5.inf
I was returned this error:
> driver bcmwl5 is already installed
When I run:
> sudo ndiswrapper -l
this error is returned:
> bcmlw5 : invalid driver!
What to do? Is there any way to remove anything and everything I've installed so far and start over from scratch? Or do I need to reformat (I guess I *could* since this is a fresh copy of Ubuntu I'm running and haven't gotten the chance to really put anything on it.)

---

### Post by kevdog on 2007-06-25
First delete the driver that you have installed.
Do this by
cd /etc/ndiswrapper
sudo rm -R *

Then make sure the /etc/ndiswrapper directory is empty.
Then proceed to reinstall your driver as you stated above (sudo ndiswrapper -i bc****)
Then check installation:
ndiswrapper -l

Make sure the bcm43xx driver is blacklisted in /etc/modprobe.d/blacklist.

Then proceed with the ndiswrapper installation steps (I hope you know them, if not please ask for help)

If the second time when you try to install the bcmwl5 driver and you get an error, please verify you have the right driver for your harder.

---

### Post by Kobalt on 2007-06-25
No need to completely reinstall your Ubuntu for that :)
First, the bcm43xx drivers can be buggy, so you may need to use ndiswrapper+windows drivers. But you must know the two don't cooperate very well, they conflict actually. So if you want to try out ndiswrapper, you should first remove the bcm43xx drivers. To do so, run these command lines :```
sudo apt-get --purge remove bcm43xx-fwcutter
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo modprobe -r bcm43xx
```
Then, I suggest you to download drivers that I'm sure work for your card [here]("http://home.nc.rr.com/thehinnants/stuff/drivers/bcmwl5.zip"). To manage this in a graphical way I recommend you to install the ndisgtk package from Synaptic. Once it's done, go into System > Admin. > Windows Wireless Drivers to install/uninstall ndiswrapper drivers. Install the ones you downloaded previously and finish by removing the possibly conflicting avahi deamon : ```
sudo update-rc.d -f avahi-daemon remove
```
You should be able to view and connect to available networks from Network Manager if all went well...

---

### Post by Globox on 2007-06-29
When I add the "bcmwl5.inf" file as the driver it doesn't show up in the installed driver menu on the left. Also I get no wireless options at all.

When I add the "bmwl5a.inf" file as the driver it DOES appear in the window on the left, but it says that the hardware isn't present.

---

### Post by Globox on 2007-06-29
I got it to work after following this guide: [http://ubuntuforums.org/showthread.php?t=405552](http://ubuntuforums.org/showthread.php?t=405552)

Thanks for the responses everyone!

---

