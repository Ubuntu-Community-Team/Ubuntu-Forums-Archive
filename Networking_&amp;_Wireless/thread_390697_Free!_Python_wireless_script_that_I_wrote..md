---
title: "Free! Python wireless script that I wrote."
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by domzo on 2007-03-22
Like other people I've had a few problems recently with the various wireless tools in Edgy (knetworkmanager, wirelessassistant etc).

I ended up using iwconfig at the command line most of the time, but that got a bit tedious so I've written a little python script that enables me to connect to any open WEP-encryped wireless network and thought I would share it here in case it's of use to anyone else. 

You can also use it to store details of networks you regularly use.

I then have this linked to a shortcut on my desktop and connecting is now a one click process. Anyway, I find it useful and somebody else might so here it is.


Some notes:

NOTE 1: This will not help with any wireless driver problems, it assumes your wireless works and it's only purpose is to make it easy to connect to various networks.

NOTE 2: It doesn't support WPA encryption, and I've not tried it on a shared key WEP network. It could be extended to handle this though I'm sure.

NOTE 3: The error reporting isn't great! When it works it works, if it doesn't it doesn't :-)

NOTE 4: It requires that you have Python and the python-wifi module (see below for how to install this).


Anyway, here's the python script:

```
#! /usr/bin/env python
import os,sys
from pythonwifi.iwlibs import Wireless 

#interface of wifi, might be eth1, wlan0 etc may need to edit this
ifid='eth1'

#pwds is a dictionary of known networks with saved keys
#it is of the form:
#{essid:[key,encoding],essid2:[key2,encoding2],...etc}
#where:
#0=hex key, 1 = ascii key

#edit this line to save your passwords:
pwds={'HOME':['123456788EEDDCCBBA', 0],'WORK':['mypassword',1]}

#now scan for networks in range

wifi=Wireless(ifid)
try:
    networks=wifi.scan()
except RuntimeError:
    print 'Must run as sudo, and have the right interface eth1, wlan0 etc set in the python code.'
    sys.exit()
except AttributeError:
    print 'No wireless networks found.'
    sys.exit()
encoding=None

#choose network from list
print '\n-------------------------------'
print 'Available wireless networks:\n'
for network in enumerate(networks):
    print '    %s) %s'%(network[0],network[1].essid)
print '-------------------------------'
netid = raw_input("\nEnter number of network to connect to (type 'none' to exit): ")
if netid in ['None','none','NONE']:
    sys.exit()
netessid=networks[int(netid)].essid
print '...connecting to', netessid

#if key is stored look it up, else ask user for input
if netessid in pwds.keys():
    key= pwds[netessid][0]
    encoding=pwds[netessid][1]
else:
    print '...passkey required'
    key=raw_input('please enter passkey (or return for no key): ')
    if key == '':
        print 'no key entered'
    else:
        print '.. is this hex or ascii?'
        encoding=raw_input('press "h" for hex or "a" for ascii: ')
        if encoding in ['a','A']:
            encoding=1
        else:
            encoding=0

#config wireless interface
print '...connecting...'
if encoding==0:
    #hex key
    os.system('sudo iwconfig %s essid %s key %s'%(ifid,netessid,key))
elif encoding==1:
    #ascii key, not really tested..
    #print 'ascii'
    #print 'sudo iwconfig %s essid %s key s:%s'%(ifid,netessid,key)
    os.system('sudo iwconfig %s essid %s key s:%s'%(ifid,netessid,key))
elif key=='':
    #no key
    os.system('sudo iwconfig %s essid %s'%(ifid,netessid))

#make dhcp request
os.system('sudo dhclient %s'%ifid)

```






USAGE:
Cut and paste the code and save it to a text file with a .py extension e.g. wifi.py then run it using python.

e.g. If you save it as /home/me/wifi.py you can run it from your home directory using "sudo python wifi.py".

When you run it, the program scans for available networks, then just follow the onscreen instructions to connect. And that's it! To save your passwords you will have to edit the python script (see CUSTOMISING section below). Also you may need to change the name of your interface in the script (again see CUSTOMISING below).


ASIDE: In fact I've saved it as "wifi" without the .py extension and put it in /usr/bin and made it executable (sudo chmod 755 /usr/bin/wifi). So now all I have to do is type "sudo wifi" from anywhere to run it. In fact I've made a shortcut on my desktop to run 'sudo wifi' :-) so all I have to do is click. But just to try it out you probably don't want to bother doing this.




DEPENDENCIES:
You need python and the python-wifi module.

python: Ubuntu comes with python, but if you haven't got it use adept/synaptic/apt-get to install it.

python-wifi: This is available as a python egg. To install eggs you will need to install 'easy_install'.

You might already have it though so check by typing "easy_install" (no quotes), if you get a 'command not found' message then you need to install it.

To do this, download [http://peak.telecommunity.com/dist/ez_setup.py](http://peak.telecommunity.com/dist/ez_setup.py) and run it using 'sudo python ez_setup.py'.

Now to install the python-wifi egg just type "sudo easy_install python-wifi". This will go to the python cheeseshop and download (and install) the latest version.

That's it. Now follow the USAGE instructions again above to try it out.


CUSTOMISING:
If you get an error you might need to change the name of your wireless interface in the script, mine is eth1. Change the line: ifid='eth1' to ifid='wlan0' or whatever your interface is called.

To add networks you use frequently add them to to the python dictionary called 'pwds'. Copy the format used for the sample networks 'HOME' and 'WORK'.

Anyway, hope that's useful for somebody! 

 DISCLAIMER:  this was just a fifteen minute job so don't expect too much in the way of robust code, error trapping etc, but it would be good to know if it works for anyone. I can't offer to support this code, but if it works for you it works! If not I'll try and help if I can but can't promise anything. Note again that this won't fix broken wireless connections but it might be a useful program for switching between networks. It doesn't do anything other wireless tools don't already do but I've found it simpler and more reliable to use (but your experience may vary).

I've got a lot out of these forums so thought I should put something back (however useful/useless it is!). :)

---

### Post by maclenin on 2007-04-01
Beaut! I am trying to teach myself (being a noob at all of this) how to put one of these together (as a bash script).... I would like mine to be "generic" - for both wired and wireless (handing all the WPAs, WEPs and other encrypted and non-encrypted) environments and to run both at start-up (from within /etc/init.d) or ad hoc from the desktop (by way of a launcher) - should I need to swap or search for network connections (of any flavor) on the fly.... As I mentioned, I am still googling to figure it all out - but your solid piece of work has given me some invaluable inspiration! Great stuff!

---

