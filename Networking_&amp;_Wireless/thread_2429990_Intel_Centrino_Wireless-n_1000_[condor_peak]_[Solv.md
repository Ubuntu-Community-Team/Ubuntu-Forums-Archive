---
title: "Intel Centrino Wireless-n 1000 [condor peak] [Solved]"
date: 2019-10-25
forum: Networking &amp; Wireless
---

### Post by britman71 on 2019-10-25
Hi,

I'm really new to Ubuntu. Just installed Ubuntu 19.10 and it appears I'm connected to my wireless network, but I cannot connect to the internet.

My wifi signal light on my laptop is constantly blinking. 

I did run lshw - C network and I see the above wireless adapter.

Any help is greatly appreciated for this Linux noon.

---

### Post by britman71 on 2019-10-25
Oh and I can see other Wi-Fi networks nearby.

---

### Post by wildmanne39 on 2019-10-25
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by britman71 on 2019-10-25
> **wildmanne39 said:**
> Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

Sorry, its asking for my password in terminal when i run the command, but nothing gets entered when i try to type.

---

### Post by britman71 on 2019-10-25
Iginore last post.  Figured how to do that

---

### Post by britman71 on 2019-10-25
here is the file

---

### Post by wildmanne39 on 2019-10-25
If you go back and read the thread at the link I gave you I think it will be a lot easier, did you run this command?
```
sudo apt install pastebinit
```
did it install pastebinit? if so then this will enable the wireless script to, upon your approval, upload the obtained data to pastebin, creating at the same time a link to it in your terminal, permitting you to paste it to a forum thread.

Once the link is created in your terminal just right click on it copy then paste it here for us to see, I am not sure how you got:

 <iframe src="https://pastebin.com/embed_iframe/G4jJTi8B" style="border:none;width:100%"></iframe> 

If you have any questions during the process just ask and I will try to help.

---

### Post by britman71 on 2019-10-25
It said it did, but I don't see it anywhere in my apps

---

### Post by britman71 on 2019-10-25
[http://<iframe src="https://pastebin.com/embed_iframe/SMjDJyD2" style="border:none;width:100%"></iframe>]("http://")

---

### Post by wildmanne39 on 2019-10-25
Please copy & paste one line at a time then hit enter to run the command, then copy the next line and hit enter and so on:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Then do:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot does it connect now?

---

### Post by britman71 on 2019-10-26
Thank you!

Wireless is now working correctly.  Can you advise what the commands did?  Also, for any future updates.  Will I have to do this again?

---

### Post by pbuckley2 on 2020-01-29
> **wildmanne39 said:**
> Please copy & paste one line at a time then hit enter to run the command, then copy the next line and hit enter and so on:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Then do:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot does it connect now?

This worked for me

---

