---
title: "Howto EVDO verizon v620"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Matty2006 on 2007-05-04
I was going to neatly compose this but I am not sure I can acurately retrace my steps and display examples as nice as other posts.. These links where the meat of getting it working.

Here are the key links that I followed in my recommended order:

Helps to get the card working in linux
[http://kenkinder.com/evdo-pc5740/]("http://kenkinder.com/evdo-pc5740/")

Helps get the scripting correct for pppd
[http://www.linuxdevcenter.com/pub/a/linux/2004/02/05/linux_cellular.html]("http://www.linuxdevcenter.com/pub/a/linux/2004/02/05/linux_cellular.html")


**Special Notes of consideration**:
1. The V620 may show up as two usb devices (ttyusb0 and ttyusb1) and in my case the common communicating interface was ttyUSB0 not ttyACM0 or ttyusb1

2. When registering the card with modprobe make sure the numbers are prefixed with "0x" for example vender=0x1410. w]When running these quiries in terminal the 0x in not shown. You can double check this info with the system info GUI by selecting the usb tree, at least in kde's system info.

3. for PPP I chose to use pppd. the other ppp may work too. (special extensions are required to make this work- which pppd has many options)

3. The call script must have **lcp-echo-failure **and **lcp-echo-interval** to stay connected to verizon. The values placed for these in the kenkinder link are likely to work but I have mine set differently. just copy what is there for linuxdevcenter.com plus these two important options.

4. use the scripting method from linuxdevcenter.com site

5. I recommend using nano as the script editor to make a new or edit pppd call file. for example:
sudo nano /etc/ppp/peers/1xevdo

6. Ignore the stuff about ifup and ifdown.. scripting works well
7. never mind the stuff about kernel patching in the kenkinder link.. unless you know something is broken in your version.

Hope this Helps :)

---

