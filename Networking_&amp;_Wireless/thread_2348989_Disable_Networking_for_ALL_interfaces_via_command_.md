---
title: "Disable Networking for ALL interfaces via command line Ubuntu 16.04 LTS"
date: 2017-01-10
forum: Networking &amp; Wireless
---

### Post by why-a-penny on 2017-01-10
So I am attempting to build a usb live iso.  In the desktop environment, its as easy as unchecking "Enable networking" within network-manager and it will disconnect all interfaces.  Then check it and it comes back up.  I would like to set it to disabled by default, while making it easy to enable by checking that box when necessary wanted.

I attempted the following:
```
$ sudo stop network-manager
$ echo "manual" | sudo tee /etc/init/network-manager.override
```

But when booting from the iso, the networking is still enabled.

---

### Post by DuckHook on 2017-01-10
Welcome to the forums, why-a-penny

In Xenial, services like network manager are controlled by systemd and no longer by upstart which is what your two commands try to reconfigure. Perhaps I'm misunderstanding your desires, but you seem to be making this needlessly complicated. If you do not want to auto-connect at startup, call up the Network Manager dialogue box&#8594;Edit Connections&#8594;Highlight the connection&#8594;Edit&#8594;General&#8594;Uncheck box: "Automatically connect to this network when it is available". Then reboot. Starting unconnected should now be your default.

---

### Post by why-a-penny on 2017-01-10
Thank you for your response DuckHook.  Is there a way to perform that task via command line?  I do not have GUI access and I am limited to shell.  Was hoping there was a very simple way to do exactly as you describe except from command line, maintaining that persist through a reboot as you described.

---

### Post by DuckHook on 2017-01-10
My mistake. You did state your CLI requirements in your title.

Ubuntu now comes with a very nice CLI tool for Network Manager called&#8213;appropriately enough&#8213;*nmcli*. You may find the following link helpful: [https://developer.gnome.org/NetworkManager/unstable/nmcli.html](https://developer.gnome.org/NetworkManager/unstable/nmcli.html)

*nmcli* can do more than the GUI applet and is quite sophisticated, offering fine-grained control and even the ability to script. However, for your purposes, the commands are simple:

[LIST=1]
[*]Find the info for your connection with:```
nmcli connection show --active
```On mine, this looks like (UUID sanitized):```
NAME                UUID                                  TYPE            DEVICE 
Wired connection 1  xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  802-3-ethernet  eno1
```
[*]To turn off autoconnect for interface:```
nmcli con mod "Wired connection 1" connection.autoconnect no
```
[*]To connect manually:```
nmcli -p con up "Wired connection 1" ifname eno1
```You can omit the -p switch for silent operation.
[/LIST]
You can either assign an alias to the last command (say: *netup*), or script it for laziness's sake.

**Caveat**: I have not actually tried these commands out for safety or efficacy, as it is just too easy to use nm-applet. Please read through the info in the link first and only invoke these commands if you have a good comfort level with them. ***Most importantly, do not do this remotely. If you lose your connection, you will be stuck.***

---

### Post by why-a-penny on 2017-01-10
Thanks for the great information!  So here is my next question, and likely the reason this seems overly complicated from my aspect.  Lets say i disable this per your post above.  This is an iso for a live usb boot.  One that i can easily put on a jump drive, take to a clients computer, plug it in and boot live into with networking disabled automatically.  Each time i plug the drive into a different computer, it could have different components which, if i understand correctly, could possibly connect by default since your post leads me to believe i would be disabling a specific connection as opposed to disabling networking completely.

So the idea is that no matter which computer i boot on, no matter how many nics it may have (for example a server with 3 or 4 NICs or a desktop with 1 eth and 1 wifi) that neither connect to any networking.  This would be to ensure that i can boot up an infected server or desktop onto live without worry about spreading through network, or booting safely on an infected network without worry about further contamination.  This is simply one scenario to sort of get the idea across.

Finallyit may be on a usb stick that is not persisted, plus I would like non-technical users to be able to simply copy the iso onto a usb and boot from it; therefore, it must be that the FRESH iso is disabled by default as opposed to a user needing to boot and THEN disable it.

Sorry for the long post, its just to iterate the need for ALL networking to be disabled by default, as opposed to workarounds such as disabling after first boot and persisting to the usb.  

Finally, the most difficult caveat here, it must still be able to connect.  This is where most of my hardache comes from because i could, of course, simply remove all drivers/software relating to network and call it a day.  But I also need to be able to have it very easy for a non-technical user to enable networking, or at the very least be able to design a script that could be set on the desktop which, when run, could enable networking.

I do appreciate your help thus far and am open to any and all ideas.  I was hoping this was going to be a simple command that mimicked the unchecking of "enable networking" within network-manager.  Sounds like this might end up being quite a spaghetti bowl of ideas and solutions, but so long as i can reach my end goal i dont mind some elbow grease scripting!

Thanks DuckHook!

---

### Post by DuckHook on 2017-01-10
You have described your needs quite well. I'm on the road right now but will give it some thought over the next few hours and respond when I get home.

---

### Post by why-a-penny on 2017-01-10
DuckHook,

  I came across these lines in a script i found online.  Looks like this may be what I need.  Perhaps you can confirm this works, but i attempted on my desktop and it did disable my eth connection.  I will attempt in my working flavor and try the iso out and get back to the forum on my results:

[FONT=&quot]```
restart_network_manager( )[/FONT]

[FONT=&quot]{[/FONT]

[FONT=&quot]  echo 'Restarting network manager..'[/FONT]
[B][FONT=&quot]  /usr/bin/nmcli networking off[/FONT]
[/B]
**[FONT=&quot]  /usr/bin/nmcli networking on[/FONT]**

[FONT=&quot]}
```[/FONT]

---

### Post by DuckHook on 2017-01-11
Yes, this is the code to turn off network manager altogether. However, your needs are rather more complex: you want it disabled by default on boot. I'm not sure that this command does so. I suspect that NM is always started by systemd as a boot process, so this setting won't survive a reboot. You may wish to test whether this is so.

A better approach, I think, would be to disable all autoconnections at boot. The network manager service is still started, but just doesn't autoconnect to anything. To do this, try the following:

[LIST=1]
[*]Create the file:```
sudo nano /etc/NetworkManager/conf.d/99-disable-autoconnect.conf
```
[*]Fill with the following:```
#Created by why-a-penny on 2017-01-10 to disable all autoconnect at startup
no-auto-default=*
```
[*]Make sure it has the proper permissions:```
sudo chmod 644 /etc/NetworkManager/conf.d/99-disable-autoconnect.conf
```
[*]Reboot. System should reboot with network manager still running, but no connections.
[*]You can always connect using:```
nmcli -p con up "Wired connection 1" ifname eno1
```Note that WIFI details are different, and even some wired connections won't be *eno1*. You can list them with:```
nmcli connection show
```
[/LIST]
If above doesn't work, you may need to disable network manager altogether at boot with:```
sudo systemctl disable network-manager.service
```This will survive reboots, but it does disable the service completely. Re-enabling is easy enough if you know the authentication password:```
sudo systemctl enable network-manager.service
```The authentication password is essential, so I don't know how this plays out with your requirement that users can start up the service. You will have to figure out if they are assigned separate passwords (which means each ISO needs to be customized), or they can all share the same one.

A final observation.

You are trying to finesse something that is highly technical and is at the core of the distro while at the same time making this a procedure that newbies can use without thought. These are incompatible objectives and I'm not sure there is a solution that will satisfy both goals. I'm of the opinion that you can have one or the other, but not both. I believe that any solution will require at least some training of your intended users.

---

### Post by why-a-penny on 2017-01-11
Some good points there.  I will attempt those next.  I have done the following for this round of testing and will post the results tomorrow.

Create a script in /etc/init.d/stopNetwork.sh
```

#!/bin/sh
/usr/bin/nmcli networking off
exit 1

```

I have also symlinked this to /etc/rc0.d/   Further, i created a script that would be placed on the default desktop called startNetwork.sh which has the same script, replacing "off" with "on".  I will see if this does the trick, idea being that while connectivity may happen initially, the time this is so should be extremely limited before the init script kicks off.

Anyway, I have not attempted anything of this sort before, so as far as i am concerned only a test will tell!  Ill come back with updates later, or, more likely, tomorrow.

Thanks again!
- whyapenny

---

### Post by DuckHook on 2017-01-11
Use of init.d is very kludgey and should be avoided if at all possible. It is a legacy of System V that systemd is designed to replace. Eventually, it will be deprecated and any scripts placed there will be orphaned. So, it's a good habit to start writing your scripts to systemd specs now. Here is a useful link to writing systemd startup scripts: [http://unix.stackexchange.com/questions/47695/how-to-write-startup-script-for-systemd](http://unix.stackexchange.com/questions/47695/how-to-write-startup-script-for-systemd)

I admire you for pushing the envelope like this in your quest for a solution. Just keep in mind the limitations of your intended userbase.

---

### Post by why-a-penny on 2017-01-13
Hey Everyone, just checking back in with updates.  

So this  method worked.  I created a simple script which disables network and  placed it in /etc/init.d/ for now with a symlink to /etc/rc0.d/  When  the user gets a desktop, the network is disabled exactly as I needed.  I  have created a second script which does the exact opposite of the  first, and enables network allowing the user to simply activate via  double clicking a desktop icon or using the Network Manager interface in  the upper right.

stopNetwork.sh:
```
 
#!/bin/sh
/usr/bin/nmcli networking off
exit 1

```

i then created the very simple startup script:
```

#!/bin/sh
/usr/bin/nmcli networking on
exit 1

```

Meanwhile I will look into proper handling via systemd.

Thanks DuckHook!

---

### Post by DuckHook on 2017-01-13
Very happy you found a solution that works for you.

Good Luck and Happy Ubuntu-ing!

---

