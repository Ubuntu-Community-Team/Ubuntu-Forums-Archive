---
title: "ubunto 9.04 how to connect to internet please help"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by brian_723 on 2009-10-27
I have just installed ubunto but cannot get on the internet .I have a speedtouch 330 sdsl modem .I do not even know if it is recognised by my computer .

i have xp also on my hard drive partioned and after i intsalled it do not find any setting to import over which was a shame .



how can a get on the net with ubunto please a big please in fact as i cannot find information anywhere .

I am with virgin and on xp so I just type in the username and password to connect to the net .

please please what can I do .

---

### Post by VoodooLoveDog on 2009-10-27
While I'm not sure, I think you need to authenticate to your provider prior to receiving the necessary information for internet access (e.g. IP Address, DNS Settings, Gateway address).

```
sudo pppoeconf
```


I believe if you run that command in terminal, you will configure your username and password for the network.

---

### Post by brian_723 on 2009-10-27
thanks very much for the reply, but i am not sure how to do this ,can you please elaborate .

---

### Post by VoodooLoveDog on 2009-10-27
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

That article will elaborate much better than I will.

---

### Post by VoodooLoveDog on 2009-10-27
Now that I'm looking at it. It seems you can just put all of this information into Gnome Network Manager under the DSL tab.

Go to: System -> Network Connections -> DSL 

Then configure your necessary information.

---

### Post by kestal on 2009-10-27
> **brian_723 said:**
> thanks very much for the reply, but i am not sure how to do this ,can you please elaborate .

You would have to use the terminal to do this, it may be a bit overwhelming at first but it gets a lot easier.

Go to Applications at the top corner, hover over Accessories, You will see a Terminal Icon. click it.

A white screen will pop up with black letters and a flashing square. type in 

```
sudo pppoeconf
```

It will ask you for your password, type that in as well.

When the information is on the screen, select it all and ctrl+shift+c (shift is needed to copy from within the terminal). Head back over to the forums and paste it like normal.


**Edit:** Eep. didn't finish my post quick enough it seems.

---

### Post by xubu_caapn on 2009-10-27
dhcpcd

---

### Post by brian_723 on 2009-10-27
thnaks guys just going to take some screen shots and go back and try again .i did get to a white box and it let me put in the command ,but it would not let me enter anything when promted for a password .

will give it a go now againn ,just got to log off and reboot .

---

### Post by eriktheblu on 2009-10-27
When prompted for your password, the terminal will not display anything you type (security feature). That's ok, just type your password and hit enter.

---

### Post by brian_723 on 2009-10-27
thnaks guys followed those instructions but it is not having it .


i got this 


found tound 2 ethernet devices 
eth0 and pan0

are all your interfaces devices listed above (eth0 and pan0 ) if no modconf will be loades so you can load card drivers or press esc to start somthing but forget 



then i scanned and got something like this

sorry I sacnned 2 interfaces,but acess concentrator of your provider did not respond ,please check your network and modem cable .
another reason for the sacn failure meybe be an other running ppoe,which controls the modem




I not even sure the macine is picking my modem .i have tried thomson 330 and bt voyager 105 .tired them bot seperatley.

i so wanted to use linux but ,no joy so far .



I also have no sound but will deal with that an other time .



please any more help would be great .


thanks

---

### Post by dj-toonz on 2009-10-27
I haven't used a speedtouch 330 for about 4 or 5 years now but there's a website called USpeedTouch Easy installation of SpeedTouch 330 USB Modems in Ubuntu and the website is [https://launchpad.net/ustouch](https://launchpad.net/ustouch) 

Hope that helps

---

### Post by brian_723 on 2009-10-29
> **dj-toonz said:**
> I haven't used a speedtouch 330 for about 4 or 5 years now but there's a website called USpeedTouch Easy installation of SpeedTouch 330 USB Modems in Ubuntu and the website is [https://launchpad.net/ustouch](https://launchpad.net/ustouch) 

Hope that helps

will give it a go thanks

---

### Post by frank cox on 2009-10-29
Try the icon next to the speaker, right click it and toggle Enable Networking.

If that does not work look in Systems-Admin-Network. If there is no such place download gnome Network manager in system-admin synaptic package manager.

Then unlock it and configure the connection. At that point you will know for sure if it found your modem.

---

