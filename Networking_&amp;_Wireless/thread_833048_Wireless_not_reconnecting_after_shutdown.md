---
title: "Wireless not reconnecting after shutdown"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by AndrewCooper on 2008-06-18
Last night I installed Ubuntu 8 on a Thinkpad T43 laptop.  It was the first time I installed Ubuntu on anything since Breezy Badger, I think.  I was very impressed at how easy the whole process was.  Everything seemed to work as expected right out of the box.  I used the Network Manager to set up a connection to the wireless network at my house and it jumped on with no fuss.  That had certainly never happened before when I've installed Linux on a machine.

So, I finished setting up and playing with my new install last night and shut the system down as I went to bed.  When I got up this morning I booted the computer up and attempted to check my email.  No dice.  I couldn't pull up any websites either.  I looked at the little "wireless" LED on the T43 that blinks when there is traffic on the wireless card but it wasn't blinking at all.  I opened the Network Manager and checked out my settings there and everything looked just like I had left it the night before.  Still wasn't connecting to the wireless network though.

I have a Windows Server 2003 box at home also, so I went over to it and made sure it was still connected.  After all, if the wireless network was misbehaving, that certainly wouldn't be Ubuntu's fault.  The Windows box connected fine and pulled up websites and email without a problem.  I still couldn't make my Ubuntu machine find the network.  Weird.

Given how easily Ubuntu installed and connected last night, I know that there has to be some way to force it to go look for a network and connect but I'm still too new to the OS to have figured it out yet.  Is there something stupidly simple that I'm just not seeing or doing?  After playing with the OS for a couple of hours last night I really, really liked it.  I just want it to connect to my wireless network without a lot of fuss, if possible.  Any help would be greatly appreciated.

Andrew Cooper

---

### Post by Cup of Squirrels on 2008-06-18
I don't use the network manager GUI, but if I remember correctly isn't there a box you can tick for "connect automatically to this network"?

Regardless, try typing into the terminal:

```
sudo dhclient wlan0
```

(Unless your device has a different I.D. - use lshw -C network to check)

If dhclient keeps sending packets and does not receive anything back, you may need to enter your details again. Try tapping them into the GUI. If this does not help, open the terminal again and type these:

```
sudo iwconfig wlan0 essid "Your Router Name In Quotes Here"
sudo iwconfig wlan0 key KEY_HERE  //Only do this if your network has encryption
sudo iwconfig wlan0 commit //This saves the info you entered on most devices
```

and try sudo dhclient wlan0 again.

If this does not work, could you post the output of "lshw -C network" please?

---

### Post by AndrewCooper on 2008-06-18
Squirrels,

I'll give that a shot when I get back home.  Thanks for responding.  I really appreciate the help.

Andrew

---

### Post by AndrewCooper on 2008-06-19
My issue was resolved.  I didn't actually go to the command line; although, I'm sure that would have worked.  I simply opened the Network Manager and set it to "roaming" then after it reconfigured I set it back to my wireless network settings.  I did have to put in the WEP Key again but no big deal.  Once it finished configuring everything again, it hopped online easily.

I think this is sort of the equivalent of disabling and then enabling the connection in Windows in order to reestablish the connection.  Regardless, it worked fairly painlessly.

Andrew

---

