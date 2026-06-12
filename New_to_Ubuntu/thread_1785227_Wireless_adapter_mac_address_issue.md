---
title: "Wireless adapter mac address issue"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by Malum Atrocitas on 2011-06-18
I seem to be having an issue with changing my mac address. I need to change my mac address for the wireless adapter I am using but it will not stay changed. When I turn on the networking in the top right corner of my screen the mac address reveerts back to the original.

What is going on and how might I fix it so that I can use what ever mac address I wish to use? 

Here is a screenshot of the problem.

[[IMG]http://img824.imageshack.us/img824/1039/screenshotmacaddressjpe.th.jpg[/IMG]](http://img824.imageshack.us/img824/1039/screenshotmacaddressjpe.jpg)

This is my first post here so be kind....:p

I am using Ubuntu 11.04

---

### Post by jtarin on 2011-06-18
[Maybe this.]("http://compixels.com/1095/how-to-spoof-mac-address-of-network-interfaces-in-ubuntu")....not certain if available yet for 11.04. You can look.

---

### Post by Malum Atrocitas on 2011-06-18
Nope still the same issue.

Is their another option to use for connecting to a wifi network for Ubuntu other than the built in utility?

---

### Post by jtarin on 2011-06-18
> **Malum Atrocitas said:**
> Nope still the same issue.Could you be a little more detailed in your procedure?

> **Malum Atrocitas said:**
> Is their another option to use for connecting to a wifi network for Ubuntu other than the built in utility?Post the output from the command "ifconfig"

Other options:[http://tuxmobil.org/wireless_unix.html](http://tuxmobil.org/wireless_unix.html)
some are in the repositories use Synaptic a search.

---

### Post by Malum Atrocitas on 2011-06-18
If you look at the original post I included a screen shot of what ifconfig showed I believe.

Basically in the screenshot I did this:

I disabled the networking in the top right corner of the toolbar. and then

1.) sudo ifconfig wlan0 down
2.) sudo macchanger --mac 00:00:00:00:00 wlan0
3.) sudo ifconfig wlan0 up
4.) ifconfig

Alright it shows the mac was indeed changed (or spoofed)
So after that I enabled the networking using the icon on the top right of the screen. After that I did ifconfig 
The output of ifconfig showed the original mac address that I had orginally wanted to change from. :x

I'm gonna try another wireless utility and see if the same thing happens.

Oh one quick question you can also change the mac address via ifconfig as well right?

Well anyways I have found a a couple solutions that I am going to give a shot to see if any will work.

Edit: I forgot to say thank you for your replies here jtarin. I appreciate your input. Hopefully I'll get to the bottom of the problem tonight.

---

### Post by jtarin on 2011-06-19
> **Malum Atrocitas said:**
> 
The output of ifconfig showed the original mac address that I had orginally wanted to change from. :x

Did you also change the MAC address in Network manager before you enabled it? I don't know how well Network Manager plays with macchanger, also there might be problem with an address of all zeros.

> To change your MAC address in Linux (and most *nix system) is easy as pie. All it takes is two easy to script commands:

 

    ifconfig wlan0 down hw ether 00:00:00:00:00:01

    ifconfig wlan0 up

 

These two little commands would set your wlan0 interface to use the MAC 00:00:00:00:00:01. Just plug in the NIC you want to set and the MAC address you want to use into the commands above and your done. Changing your MAC address is one of those things that is much easier to do in Linux then under Windows.
IT WILL ONLY STAY THAT WAY UNTIL YOU BRING THE CONNECTION DOWN.

---

### Post by jtarin on 2011-06-19
[Here's some ideas]("http://www.linuxquestions.org/questions/linux-newbie-8/how-to-permanent-spoof-fake-mac-address-for-eth0-and-eth1-in-new-linux-distro-s-779579/")......personally I don't use Network Manager...I think it's a piece of non-wonderment.:p

---

### Post by fractalman on 2011-06-19
i never seem to have any problems with changing my mac, what has been suggested already should work but you could try this variation on the code, its what i use for my eth0 mac address, im 0n 11:04 so it should work,



```
sudo ifconfig wlan0 down
```

```
sudo macchanger -r wlan0
```

```
sudo ifconfig wlan0 up
```


just a guess here but could it be the mac doesn't display as changed because you never started the wifi back up before trying 'ifconfig'? - if someone else could verify this, or not as the case may be because i'm not sure if it would make a difference.

---

### Post by jtarin on 2011-06-19
> **fractalman said:**
> 
just a guess here but could it be the mac doesn't display as changed because you never started the wifi back up before trying 'ifconfig'? - if someone else could verify this, or not as the case may be because i'm not sure if it would make a difference.
Good Point! +1

---

### Post by Malum Atrocitas on 2011-06-19
Thank you!

I solved the problem last night by using wicd to connect rather than standard network manager that ubuntu comes with.

Yeah your right jtarin the integrated network manager is rather lame.

[quote='fractalman']just a guess here but could it be the mac doesn't display as changed because you never started the wifi back up before trying 'ifconfig'? - if someone else could verify this, or not as the case may be because i'm not sure if it would make a difference.[/quote]

You can actually see in the screeshots where I had forgotten to ifconfig up. It just purely didn't show the whole interface which i noticed immediately. and then ifconfig wlan0 up it shows the changed mac address! :guitar:

But my problem lies with the network manager that comes with Ubuntu. Because once I change the mac address and verify that it is indeed changed ,(or spoofed), when re-enabling networking in the manager it reverts the mac back to its original address. :(

So all in all problem solved I just won't use the network manager that is integrated with Ubuntu. :p

---

