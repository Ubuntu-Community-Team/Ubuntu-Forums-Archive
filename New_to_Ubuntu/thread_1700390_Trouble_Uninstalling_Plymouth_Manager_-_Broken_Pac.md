---
title: "Trouble Uninstalling Plymouth Manager - Broken Packages?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by jonbwilson on 2011-03-04
Noob here, hence the reason I'm posting this in the Absolute Beginner forum.

Anyway, I installed Plymouth Manager because I wanted to change my splash screen in Ubuntu 10.10. I didn't really like the interface so I ended up going with Zorin Splash Screen Manager instead.  Now when I try to uninstall Plymouth Manager, I get a series of error messages in the Software Center that basically tell me to go jump off a bridge.  When I try to uninstall it in Terminal, I get the following:


jon@jon-PC:~$ sudo apt-get remove plymouth
[sudo] password for jon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 erlang-crypto : Depends: erlang-base (= 1:13.b.3-dfsg-2ubuntu3) but it is not going to be installed or
                          erlang-base-hipe (= 1:13.b.3-dfsg-2ubuntu3) but it is not going to be installed
 erlang-syntax-tools : Depends: erlang-base (= 1:13.b.3-dfsg-2ubuntu3) but it is not going to be installed or
                                erlang-base-hipe (= 1:13.b.3-dfsg-2ubuntu3) but it is not going to be installed
E: Broken packages
jon@jon-PC:~$ 


Obviously since I'm a noob I have no idea what any of this means.  If somebody could translate and provide a suggestion I would be very grateful.  Thanks!

---

### Post by dennmac on 2012-09-23
I've just made the same mistake, of installing the Plymouth Manager. It never installed properly, can't be updated, and Update gives me errors about fetching files from 'mefriog'... 

ERROR###ERROR###ERROR###ERROR###ERROR###ERROR###ERROR
W:Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

It's a shame no one has posted anything that might help us get rid of all this!

---

### Post by daslinkard on 2012-09-23
Do not remove "plymouth" as you say carries packages with it that are vital. Go to synaptic type plymouth in search window and go to "plymouth themes" choose the theme you want looks like text and install it. (Make sure it is a Plymouth Theme) Now run below in a terminal and pick out theme you wish to use by the number.
```
sudo update-alternatives --config default.plymouth   
```Once you have chosen and installed now run below:   ```
sudo update-initramfs -u
``````
sudo reboot 
```

---

