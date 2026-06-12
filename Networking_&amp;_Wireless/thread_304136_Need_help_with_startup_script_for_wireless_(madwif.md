---
title: "Need help with startup script for wireless (madwifi+WEP)"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by cyangecko on 2006-11-21
Hello,

After having to reinstall Dapper, I have lost my wireless.  I compiled madwifi and now have wireless again.  The only problem is whenever I restart the computer, I must input the following lines in terminal before my wireless is up and running:

sudo modprobe wlan_scan_sta
sudo iwconfig ath0 essid "my_network"
sudo iwconfig ath0 key my_key
sudo dhclient ath0

And then it works.  
for my /etc/network/interfaces  I have the following

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
  pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
  wireless-essid my_network
  wireless-key my_key

auto wlan0
iface wlan0 inet dhcp


Do I need to add/omit anything from this file, or is there a way I can create a script to initialize my wireless upon startup, and if so how would I go about doing this?

Thanks in advance.

---

### Post by FrodoB on 2006-11-21
On Dapper, using the normal install CD you do not need to compile anything to have madwifi, Atheros devices just work out of the box. If you used the alternative CD you would have to install the linux-restricted-modules.

You issue may be due to trying to compile drivers when they are likely already there.  My DWL-G650 just works out of the box.

The interfaces section should look like this:

iface ath0 inet dhcp
wireless-essid My_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto ath0

It also works out of the box on Edgy as well.

---

### Post by cyangecko on 2006-11-21
FrodoB- 

Thanks for the quick reply.  Unfortunately my device has not worked straight out of the box, edgy or dapper.  I had it working beautifully in dapper before I had to reinstall. Edgy was too much of a hassle with wireless so went back to dapper.  My wireless is built in - Atheros AR5006.  Again,  after I enter those lines in terminal, everything works, so still looking for a better solution.

---

### Post by trubblemaker on 2006-11-21
I've seen sometimes that ath0 needs a shake before it gets going try adding

```

iface ath0 inet dhcp[COLOR="Red"]
pre-up ifconfig ath0 up
pre-up ifconfig ath0 down[/COLOR]
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta # don't know what this but see if the added pre-ups corrects you and consider removing this.
wireless-essid my_network
wireless-key my_key

```


it might add time to your boot.   The alternativly you could add the command lines that work to a script 
```

iface ath0 inet dhcp[COLOR="Red"]
post-up /path/to/script [/color]
wireless-essid my_network
wireless-key my_key

```
This slows down my boot but hey give it a shot if you need it to work on boot.

---

### Post by cyangecko on 2006-11-22
trubblemaker, 

I will try to see if that fixes the problem.  

You mentioned:
> **trubblemaker said:**
> 
it might add time to your boot.   The alternativly you could add the command lines that work to a script 
```

iface ath0 inet dhcp[COLOR="Red"]
post-up /path/to/script [/color]
wireless-essid my_network
wireless-key my_key

```


I have read that in other threads, but my question is path to *what* script? I don't know of a script that incorporates those elements for startup, nor do I know how to create one.  How would I go about doing so and what exactly do i need to include?

Thanks.

---

### Post by trubblemaker on 2006-11-22
good question, I was saying that you should create a script  here's how you do that:

with your favorite editor create a text file with this

```

#/bin/bash
#above line must be first line in the file, this is true for all scripts
# <-- other than the first line means comment and isn't run by computer
# list all the commands that you want to run below.  
# Just like your typing them into a command prompt
sudo modprobe wlan_scan_sta
sudo iwconfig ath0 essid "my_network"
sudo iwconfig ath0 key my_key
sudo dhclient ath0

```

after you're created the file called say "network_script" saved to "/path/to/script/network_script" (here "/path/to/script" is an example, it's more likely to be something like "/home/user-name")

then you need to in a command terminal in the directory "/path/to/script/" you need to make the file executable so you change the permissions
```
chmod u+x network_script
```

now you can run the script by typing "/path/to/script/network_script" or by tuping "./network_script" if your terminal is in "/path/to/script/"

now you can make the changes I talked about in previous post.  Hope this helps, if you have questions just ask.

---

### Post by cyangecko on 2006-11-26
trubblemaker,

Just got back home to my computer after a long weekend away.  I tried out your suggestion and it worked for the most part.  Whenever I type /path_to_script while in terminal it works (requires password), however it does not start wireless at startup.  I am wondering if it has anything to do with the fact that the commands include sudo and need a password?  I also tried adding it to my startup in sessions, but no go.  Any suggestions?

---

### Post by cyangecko on 2006-11-26
Another note-

After I did the chmod u+x /path_to_script, I noticed that when I tried to open a file as root, it was incredibly slow.  I researched this on the forums and it looks like it has a direct connection with my wireless problem.  Here is the link.

[http://www.ubuntuforums.org/showthread.php?t=86838]("http://www.ubuntuforums.org/showthread.php?t=86838")

For the meantime I am removing the chmod and taking it out of session startup until I find a better solution.

---

### Post by spd106 on 2006-11-26
It's rather odd that the wlan_scan_sta module needs to loaded, it should be done when the others are. Have you tried regenerating the module dependencies, ie **sudo depmod**?

Also you might want to either check whether any vap interfaces have already been created or just destroy any that might be there, before creating a new one blindly in the script. ie **sudo wlanconfig ath0 destroy**.

There's no need to have a sudo on every line if you have already called the script with root privileges, which you will have to since these commands require it.

---

### Post by cyangecko on 2006-11-26
spd106

Yes, you are correct, I don't need to reload the wlan_scan_sta module.  Still without that same issues.  What do you mean by regenerating the module dependencies (what will it do and what will it change and is there anything I will need to redo afterward?)

I am not exactly sure what you mean by vap interfaces.  Once I hit sudo wlanconfig ath0 destroy, what will happen?

Will try adjusting the script as you suggested.  Thanks for the input.

---

### Post by spd106 on 2006-11-26
When modules are loaded into the kernel through modprobe, the modprobe utility checks which other modules should be loaded as well. It does this by checking the dependencies. By calling depmod you refresh these dependencies, which is advisable when you install new driver modules.

I suggest that you have a read through the user docs on [http://madwifi.org](http://madwifi.org) for information on how to use wlanconfig. I'm no expert, though I have been using it recently for monitor mode and ad-hoc vaps (virtual access points).

Going by the details from your first post it looks like all you doing is re-entering the details from the interfaces file. Perhaps you should scrutinize the interfaces file closely to check for spelling mistakes in the encryption key. I've made that mistake many times in the past. I also think it's worth commenting out the wlanconfig line as well.

---

### Post by cyangecko on 2006-11-26
I will look over that information.  Thanks for the tips.  I managed to screw more stuff up by trying to fix this wireless issue, so I am reinstalling ubuntu, and starting over.  I appreciate everyone's comments.  Hopefully will get this thing figured out.

---

### Post by cyangecko on 2006-11-26
UPDATE---

Reinstalled Dapper.  
No recognition of my Atheros AR5006xs chip out of the box.
Followed the HOWTO on [http://madwifi.org/](http://madwifi.org/) 
Reboot= same problem.

Still, after rebooting, I must type in terminal:
sudo iwconfig ath0 essid "my_network"
sudo iwconfig ath0 essid my_key
sudo dhclient ath0

and then wireless resumes, but doesn't hold these settings upon reboot.

I am stuck here.  Tried the script (messed up my sudo).  Tried setting up WPA instead of WEP but was even more of a problem.  I would like to be able to automatically connect to my wireless upon startup without using the terminal.  Simple solution?  Any solution?

---

### Post by trubblemaker on 2006-11-26
eh means run:
```
sudo depmod
```
if rebuilds the module depenencies.
fyi if you run a script from /etc/network/interfaces it runs with root privelages. also you could try add the following to the top of the script 

```
 ifconfig ath0 up
ifconfig ath0 down
ifconfig ath0 up

```

Not sure what you mean with root opening the script just try adding the "chmod u+x " to the script and running it in a terminal. if it works great if it doesn't work it will give you output to why.

then add it to /etc/network/interfaces after it's working in the terminal with the changes mentioned above. Let me know how it goes.

---

### Post by trubblemaker on 2006-11-27
ok, make script
```

#/bin/bash

sudo iwconfig ath0 essid "my_network"
sudo iwconfig ath0 essid my_key
sudo dhclient ath0

```
then:
```

chmod u+x script_name

```
then add it to your startup

click on >System>Prefernces>Session>Startup Programs>

enter the path to the script. Then it will run when you log in.  Bye that time ath0 should be awake.   

**Alternative, **I've seen issues with it being slow to wake up.
usually fixed with adding 
```
pre-up ifconfig ath0 up
pre-up ifconfig ath0 down
```
to the interface entry in /etc/network/interfaces.

---

### Post by cyangecko on 2006-11-27
trubblemaker-

Thank you so much for your help.  Things are finally running from startup.  Somehow the problem fixed itself without needing a script (only took about 5 reinstalls to get it working correctly).  So I don't know what managed to happen, regardless I am happy it works.  Again, I appreciate your patience and explanations, it has helped me get a better grasp on the workings of things.

---

### Post by trubblemaker on 2006-11-27
hey if you are a mad re-installer like myself I might also pass on one more bit of info.  Setup a different partition for your home directory, this allows you to maintain data between installs and even keep settings like your book marks in firefox.  IT's really handy especially if you like to mess around.  Or thin things out (like packages you don't need).

---

