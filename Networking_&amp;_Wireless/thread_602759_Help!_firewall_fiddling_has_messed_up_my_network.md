---
title: "Help! firewall fiddling has messed up my network"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by mckechan on 2007-11-04
I was fiddling around with differnt firewalls, namely guarddog and fwbuilder. I didn't really get anywhere so I apt-get removed after experimenting.

I have a firewall in my router anyway.

Well next time I start my computer (I use feisty btw) I have no network. I think all the ports are blocked from reveicing. I am sure my actual network settings haven't been changed.
[I]
sudo /etc/init.d/networking restart[/I]

I get
[I]
SIOCADDRT: File exists
Failed to bring up eth0 [OK][/I]

Please help!

---

### Post by mckechan on 2007-11-04
when i look at the system monitor it seems i am receiveng data but not able to send any...

---

### Post by mckechan on 2007-11-08
Well I had to hose my box. Installed gutsy from scratch.

Every thread I found with similar errors had no solutions and judging by the lack of replies it is a bug of sorts.

---

### Post by ruibernardo on 2007-11-08
Hi Mckechan,

you shouldn't install two firewalls (as you now know). If you do want to try another firewall, uninstall the one you have, **reboot** and then install the other. That's the complicated way.

The simple way:

1. Uninstall the actual firewall (for example guarddog):
```
sudo apt-get remove guarddog
```2. Clear your iptables rules  (man iptables):
```
# a reboot without any firewall installed will also clear any iptables rules.
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
sudo iptables -X
```3. Verify your iptables rules with "sudo iptables -L". You should get something like:
```

user@gutsy:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
user@gutsy:~$ 

```Now you have no rules set in iptables. 
4. Install fwbuilder:
```
sudo apt-get install fwbuilder
```Repeat step 1 with fwbuilder and install another one.

Remenber that if you purge the packages you install ("sudo apt-get remove guarddog **--purge**" or "Mark for complete removal" in Synaptic), you will remove all the configuration files (useful if you messed up with them). If you just remove without "--purge", the configuration files on disk will not be removed and those will be used next time you install that package (no configurations lost if you don't use --purge).

I hope this helps you this time. :)

---

### Post by mckechan on 2007-11-08
Thanks for the reply. I did try some of those things before (iptables INPUT ACCEPT etc) as my friend is a sys-admin and helped me a bit online. However, nothing seemed to work. I probably should have used --purge when I removed everything.

Anyway, as I said I gave up and installed gutsy. 

I've been a noob for about a year now and I am one to fiddle so I have had a few times when I messed up my box but this is the first time i've needed/decided to reinstall in ages!

---

### Post by ruibernardo on 2007-11-08
More about settings and problems with them.

NOTE: firewalls generally don't do this! Only applications that users run.

Some packages have their system configuration files in /etc/ and when an user runs the program, they create a hidden file or directory on the home directory of that user, where all personalised settings of that users are stored.

In the case you mess with something (as a normal user) and you want the program to behave as it was run the first time, search for the configuration file/directory in your home. Usually it's ~/.name_of_the_program. You can find them pressing Ctrl+H in Nautilus or running:

```
ls -la ~/.name_of_the_program*
```Rename or delete it (rename it if you want to test something and don't want to loose your actual settings for some reason). The next time you run that program, a new file or directory is created and all previous settings are forgotten. Close the program, delete the new file and rename the backup settings back to the original name to restore your previous settings.

Cheers.

---

