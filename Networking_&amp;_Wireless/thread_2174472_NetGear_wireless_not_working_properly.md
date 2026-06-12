---
title: "NetGear wireless not working properly"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by Thijs_Wouters on 2013-09-14
Hi

I have a NetGear wireless usb adapter. But it only works for a few moments before the connection seems to be lost. I still have a connection to the router but there is no connection to the internet (other devices connected to the same router keep on working). When I turn it off and on again, it again works for a little while.
What can I try to troubleshoot this? I have Ubuntu 13.04.
Thanks for any help you can give.

---

### Post by varunendra on 2013-09-15
Hi ! And Welcome to the forums :)

Please follow the "Wireless Script" link in my signature, download the script and run it when the connection seems to be lost. Post back the report that the script generates.

If copy-pasting the output code here, please use 'Code' box to do that. Follow the "Using Code Tags" link in my signature to see how. Thanks.

---

### Post by Thijs_Wouters on 2013-09-15
Hi, thanks for the welcome.
I attached two tarballs. One for when the internet was working and the other for when the internet just broke.
If you need anything else, just ask.
And thanks.

---

### Post by varunendra on 2013-09-16
There are too many usb entries in your udev rules file. Although this doesn't sound like a reason to the problem you described, but may cause other issues. Let's generate a clean one first, then reload your driver with a parameter supposed to help -

Open a terminal (Ctrl-Alt-T) and do -
```
cd /etc/udev/rules.d
sudo mv 70-persistent-net.rules 70-persistent-net.rules.bak
sudo udevadm trigger
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=1
```

Is the connection any better? The last command forces a temporary change that will be lost at next boot. If it helps, we'll make it permanent.

If the above alone does not help, please change the encryption type in your router to pure WPA2-PSK with AES encryption. No WPA/WPA2 mixed mode, no TKIP. Also, it seems that your router has N-channel enabled. It does not work well with some Linux drivers sometimes. So also disable it (use b/g only mode) - permanently if that is not a problem for you, or at least temporarily for a test.

Once the above is done, run the last two "sudo modprobe..." commands again, and let us know how it goes.

Oh, and before posting again, please also check -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
Is the newly generated file there? With only one entry pertaining to USB this time?

---

### Post by Thijs_Wouters on 2013-09-17
Now it seems to be working. What do I need to do make it permanent?
And the file now only contains one USB entry.

---

### Post by Hadaka on 2013-09-17
Hi, to make it permanent please do..
```
sudo su
echo "options rtl8192cu swenc=1" > /etc/modprobe.d/rtl8192cu.conf
exit 0
```
boot

---

### Post by varunendra on 2013-09-17
Yep, please do what Hadaka suggested.

---

### Post by Thijs_Wouters on 2013-09-18
Thanks a lot.

---

### Post by Hadaka on 2013-09-18
Glad that worked for you !
enjoy!

---

### Post by Thijs_Wouters on 2013-10-02
It is no longer working. It is even worse now. I cannot connect to the secured wireless. And the current connection drops out every few minutes.
I ran your script and attached the output.

---

