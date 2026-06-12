---
title: "Opening Port in Transmission"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by carolina on 2011-05-18
I am  new to use torrents in general and would like to try Transmission . In Transmission Preferences under the Network tab & Incoming i did the port test and my port is closed . The number 51412 is shown . How do i open/activate it ?   :)

Thanks

---

### Post by wojox on 2011-05-18
Do you have a router? You would need to configure it there.

---

### Post by carolina on 2011-05-18
No , i connect directly to  a cable modem . Could this be some sort of firewall issue and if so how would i get to the firewall ?

---

### Post by wojox on 2011-05-18
What does this return:

```
sudo ufw status
```

---

### Post by carolina on 2011-05-18
Inactive

---

### Post by wojox on 2011-05-18
> **carolina said:**
> Inactive

That's the default installed firewall for Ubuntu. Did you install another?

What type of cable modem is it?

---

### Post by carolina on 2011-05-18
I am using Ubuntu 10.10 and i haven't intentionally installed another firewall . There are other users on the computer however so i suppose it's possible . As for the cable modem i am in the Philippines so not clear on what is meant by "type" .  Sorry

---

### Post by jtarin on 2011-05-18
On the same dialogue you see your port number is the box that says "Use UPnP or NAT-PMP port forwarding from my router checked...or unchecked?

---

### Post by carolina on 2011-05-18
Checked

---

### Post by wojox on 2011-05-18
> **carolina said:**
> I am using Ubuntu 10.10 and i haven't intentionally installed another firewall . There are other users on the computer however so i suppose it's possible . As for the cable modem i am in the Philippines so not clear on what is meant by "type" .  Sorry

Are you a regular user or admin? By type I meant brand.

---

### Post by carolina on 2011-05-18
I am the admin so don't see how anyone else could have altered firewall . The modem brand is Scientific Atlanta and it's worked fine with previous versions of Ubuntu .

Just wondering if something went amiss when i installed or if it could be due to updates . All updates are current . I am currently downloading an avi file via a download manager but wouldn't see the relevance but then i have also been having issues with burning cd/dvd , again perhaps not related ?

---

### Post by wojox on 2011-05-18
What happens when you go here in your browser [http://192.168.100.1/](http://192.168.100.1/)

---

### Post by carolina on 2011-05-18
[LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Name**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] WebSTAR DPC2100R2[/SIZE][/FONT]               [LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Modem Serial Number**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] 211310414[/SIZE][/FONT]               [LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Cable Modem MAC Address**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] 00:1b:d7:12:65:62[/SIZE][/FONT]               [LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Hardware Version**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] 2.1[/SIZE][/FONT]               [LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Software Version**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] v2.0.2r1256-060303[/SIZE][/FONT]               [LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Receive Power Level**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] -5.5 dBmV[/SIZE][/FONT]               [LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Transmit Power Level**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] 51.0 dBmV[/SIZE][/FONT]               [LEFT][FONT=Arial][SIZE=2][COLOR=#000000]**Cable Modem Status**[/COLOR][/SIZE][/FONT][/LEFT]
     [FONT=Arial][SIZE=2] Operational[/SIZE][/FONT]

---

### Post by carolina on 2011-05-18
I goggled installing Ubuntu 10.10 firewall  and followed the instruction which had me use the Softwear Center to down & configure firewall . Using the sudo command the firewall is now active . However , i still have a closed port when checking transmission so perhaps will try a reboot .

---

### Post by carolina on 2011-05-18
> **carolina said:**
> I goggled installing Ubuntu 10.10 firewall  and followed the instruction which had me use the Softwear Center to down & configure firewall . Using the sudo command the firewall is now active . However , i still have a closed port when checking transmission so perhaps will try a reboot .
Problem solved... i think   ;-)

transmissions port still shows as closed but it is downloading so will see how it goes .

thanks for the efforts guys

---

