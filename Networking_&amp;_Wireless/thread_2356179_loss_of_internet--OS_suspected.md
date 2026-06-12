---
title: "loss of internet--OS suspected"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by lshepley on 2017-03-20
I am running Ubuntu 16.04 on a 32bit machine.  The operating system has been kept up to date according to the from time to time recommendations which “arrive” automatically.
 
 
 Starting a week or so ago, my internet access started to fail.  Strangely, I have it for a while after the machine is turned on, then lose it.  I get the “no access” screen.  Changing the dongle that receives the signal changes nothing nor does change to USB port, and, anyway, I can always log in to the router so the wireless is working at least to the router.  I have another computer (64 bit 16.04) which is always on and always works perfectly (including with the “defective” dongle), as do numerous other wireless gadgets.  (Due to a judgement error, I bought and new router as a possible solution, and that did no good.)
 
 
 One thing which makes me suspect the operating system in my machine is the fact I got a notice that an update was incomplete.  Of course, I couldn’t complete it because I couldn’t download what I needed.  In the few minute the internet has been available for me, I couldn’t get the notice again.
 
 
 Periodically, I make a clone of the hard drive (using “dd”), and I did so a few months ago.  I just booted the machine using the clone, and it is working perfectly and has been for some time.  I believe this eliminates the obvious theories suggesting heat or other hardware failures.  My conclusion is the operating system as loaded (incompletely apparently) to my machine, but I’m open to a better theory.  I’m also open to a suggestion about how to solve my problem.
 
 
 Thanks very much.

---

### Post by praseodym on 2017-03-20
Please run the wireless-script from the sticky thread and show the outputs here

---

### Post by lshepley on 2017-03-21
Thanks; I will when I make a connection.  They only last a minute or two.

---

### Post by lshepley on 2017-03-22
I hope this is what you asked for; as you've probably guessed, I'm unfamiliar with all this.  I wasn't allowed to post this.   I did run update and upgrade.

By the way, I am able to wirelessly access another ubuntu machine through the router.  

I now have a wired connection, which enables me to work through the internet, so I can fully follow your instructions.  Also, is there a way for me to reinstall the operating system without disturbing special things in /dev and /etc.

Thank you very much.

lew@uus:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
> chmod +x wireless-info && \
> ./wireless-info
--2017-03-22 15:28:22--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2017-03-22 15:28:23--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.44.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.44.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info       100%[===================>]  15.78K  --.-KB/s    in 0.02s   

Last-modified header missing -- time-stamps turned off.
2017-03-22 15:28:23 (972 KB/s) - &#8216;wireless-info&#8217; saved [16156/16156]


Results saved in "/home/lew/wireless-info.txt".

Results also archived in "/home/lew/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:

[http://paste.ubuntu.com/24230649/](http://paste.ubuntu.com/24230649/)

---

### Post by praseodym on 2017-03-23
Please run the script again with the cable unplugged. For LAN this may help
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
and reboot. For the incomplete update:
```

sudo apt-get update
sudo apt-get -f install
sudo dpkg --configue -a
```

---

### Post by lshepley on 2017-03-24
Please understand I don&#8217;t know what I&#8217;m doing, but I do have a theory that seems to explain (sort of) my problems and through which (or luck) my problem was solved.
 
 
 I had tried to solve an earlier problem by buying a new router.  My wireless group consists, among other things, of two ubuntu computers, and to facilitate their communication with each other I had maintained permanent IP addresses on them.  One is ethernet wired with a wireless &#8220;backup&#8221;; the other was wireless only.  In the course of installing the new router and trying to figure out if I&#8217;d solved my earlier problem, I ran a wire to the purely wireless computer, and I switched back and forth several times, sometimes using both wireless and ethernet.  I also tried several receiver dongles.  They of course had different MAC addresses, but the computer names remained the same.  I think the router was totally confused about who was who, producing the weird situation (which I found no setting for) of wireless reception of the router and the other computer but no internet access in one (and only one) of the computers.
 
 
 I am really grateful to anyone who bothered at all with my problem, and I apologize for my ignorance.  Maybe if someone has as similar problem and is as hopeless as I, this might help.

---

