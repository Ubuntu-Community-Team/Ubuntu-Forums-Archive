---
title: "a lill help for a Nub :P"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Ominae on 2007-10-01
Hi there guys 

okay here is my prob.
I have jus dropped Ubuntu on to my old Presario 700 laptop, due to it being a faster OS even on older systems.  I have managed to scrape through installing things myself so far as i would rather learn than ask for help but now i a, lost.
I have an Inexq MRo54g (Ro2) wireless card
i have been trying to install it the Ubuntu version i am using is the newst from the site :S sorry dun know.  i read up a bit an tryed to get it working b4 this post so far i have managed to get the nids wrapper *whatever it is spelt* installed and downloaded the Ubuntu drivers for the card but trying to install the drivers i just dont know what i am doing.  the laptop pics up the card an sees the networks arround me but can do no more.

iff any one can give me some advice that would be grand 


P.S( i know this is the networkin section but since installin the wrapper my shut down button no loger works it locks the descktop as in nuttin can be clicked on utill i hit enter then it is normal aggen :S dunno what i dun )

---

### Post by Vadi on 2007-10-01
Hm... I had that problem, where all networks would be seen, but Network Manager couldn't connect. You can give wicd ([click]("http://wicd.sourceforge.net/")) a try, it works better on some cards and actually connects.

---

### Post by cameronjcc on 2007-10-01
What driver are you using?
If it's not (MR054g-R02_Linux-STA-1.4.5.0.zip)
that might be your problem.

---

### Post by maybeway36 on 2007-10-01
I wish you could do this through Restricted Drivers Manager, since that's sort of what its made for. :P Well, that can wait till April I guess...

I think the commands are like:
```
sudo ndiswrapper -i yourdriverfile.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

Then you might have to edit /etc/network/interfaces if it doesn't work yet.

```
sudo ndiswrapper -l
```
tells you if the drivers are installed or not.

---

### Post by Ominae on 2007-10-01
> **Vadi said:**
> Hm... I had that problem, where all networks would be seen, but Network Manager couldn't connect. You can give wicd ([click]("http://wicd.sourceforge.net/")) a try, it works better on some cards and actually connects.



Hey Vadi 

many thanx took me an hour to work out what i was doing to get this to o=work right :) 
but it works :P now i jus need to get it to hook up to my netgear router :) hehehe  not 
quite sure what is goin on but there is unsecure net to use :P hehe

---

### Post by Vadi on 2007-10-01
I have no idea what do you mean. Press the "prtsc", (print screen) button to take a screenshot and post it.

---

### Post by Ominae on 2007-10-03
Okay gettin realy bummed now :S 

i had the Wicd workin for a few days now it is not workin at all 

I wont connect get ip what ever i got no wifi agen :S 

i have installed the Ndiswrapper and Wicd        Wicd woroked for a few days 

now nuttin 

i downloaded the MR054g-R02_Linux-STA-1.4.5.0 drivers an well instalin them is jus not gonna happen i jus dunno what i am doing with them can any one point me to a moon guide for this b4 i have to go back to windows jus to get a net connection i jus dun get what is goin wrong if yu need info from me tell me how to get what yu ned an i will get it an post it 

but for now Ubunt is jus one big source of anguish that i am gettin close to getttin rid of :S i need my net agen

---

### Post by cameronjcc on 2007-10-10
I did this, but yours isn't the same, but you might be able to use this as reference:

1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines

# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"

Remove all comments ('#') that you see so that all devices arehandled by the default network manager.

I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper

Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.

You could also type "sudo apt-get install ndiswrapper-utils 
(IF you are not using ubuntu then make sure you have ndiswrapper-utils somhow installed)

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"

Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"

Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit.

---

