---
title: "Connecting to Ubuntu via Android phone"
date: 2015-11-14
forum: Networking &amp; Wireless
---

### Post by k0tt0n on 2015-11-14
I'm trying to connect my android phone to Ubuntu over wifi via the app ES File explorer and Samba. I can see the laptop with Ubuntu installed with the app but cannot connect. I have set a user and password in Samba with my /home/user/Downloads dir with read/write permissions. Each time I enter my username and password in ES File Explorer it won't connect. I don't get any messages, just the username/password box resets.

Is there anything I can type in the terminal to give you an idea of what’s going on?

thanks

---

### Post by TheFu on 2015-11-14
Instead of samba, would you consider sftp?   Just load  openssh-server and fail2ban, then any sftp client can be used. If you open the ssh port on the WAN, then you can access files from anywhere in the world, securely. Just make certain you use ssh-key-based authentication if you enable the internet part.

---

### Post by k0tt0n on 2015-11-14
> **TheFu said:**
> Instead of samba, would you consider sftp?   Just load  openssh-server and fail2ban, then any sftp client can be used. If you open the ssh port on the WAN, then you can access files from anywhere in the world, securely. Just make certain you use ssh-key-based authentication if you enable the internet part.

I'd prefer to just open an app on the phone and connect to transfer files without having to start anything on the laptop. 

thanks for the suggestion though.

---

### Post by TheFu on 2015-11-15
> **k0tt0n said:**
> I'd prefer to just open an app on the phone and connect to transfer files without having to start anything on the laptop. 

thanks for the suggestion though.

Are you familiar with ssh?

sftp works like that, plus I always think of samba as a security risk, but not ssh. ssh-server runs as a daemon and is used by every unix admin around the world daily.  ssh (and sftp) are considered secure.  samba is not.

If you are running samba on a laptop, you need to turn it off whenever you leave the household LAN. With ssh-server and fail2ban, that really isn't necessary, provided strong passwords are used or ssh-keys.

---

### Post by Morbius1 on 2015-11-15
> **k0tt0n said:**
> I can see the laptop with Ubuntu installed with the app but cannot connect. [COLOR=#0000cd]I have set a user and password in Samba[/COLOR] with my /home/user/Downloads dir with read/write permissions. Each time I enter my username and password in ES File Explorer it won't connect. 

Any user or the user specified by the path /home/[COLOR=#0000cd]**user**[/COLOR]/Downloads?

What I'm thinking is that perhaps you encrypted your home directory so the only user that will gain access to the folder - locally or through samba - is [COLOR=#0000cd]**user**[/COLOR].

The only other quick thing I can think of is a rather common bug in the install process where a parameter in smb.conf is set to the wrong value. Run this command:
```
testparm -s | grep "encrypt passwords"
```
If it comes back with nothing you are good but if it comes back with:
> encrypt passwords = No
Edit /etc/samba/smb.conf and change the No to a Yes.
Then restart smbd:
```
sudo service smbd restart
```

---

### Post by SeijiSensei on 2015-11-15
I use [Wifi File Transfer Pro]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en") occasionally, but you need to start the app on the phone, then open a browser on the destination device.  I've also used [AndSMB]("https://play.google.com/store/apps/details?id=lysesoft.andsmb&hl=en") to connect to a machine running Samba.

Most of the time I just use a USB cable.

---

### Post by howefield on 2015-11-15
Not a direct answer to your samba question, Morbius1 is doing that admirably,  just to mention I also use ES File Manager but using the sftp option to access any of my machines that has ssh installed, it's simple easy and quick. If controlling the android device from an Ubuntu machine, the Remote Manager in ES File Manger is a great option.

---

### Post by k0tt0n on 2015-11-16
> **howefield said:**
> Not a direct answer to your samba question, Morbius1 is doing that admirably,  just to mention I also use ES File Manager but using the sftp option to access any of my machines that has ssh installed, it's simple easy and quick. If controlling the android device from an Ubuntu machine, the Remote Manager in ES File Manger is a great option.

thanks for the reply guys.

I've installed ssh and managed to work out how connected via sftp using es file explorer. :D

---

### Post by TheFu on 2015-11-16
Just for a little clarity.  

sftp **will** be slower than samba. Speed of transfer often isn't THAT important.  Start a transfer, make some coffee and it is done when you get back. Not a big deal.

But the ability to have access to files securely from anywhere you have interent makes up for that slight speed hit, IMHO.  Securing sftp happens when you secure ssh. Be certain that you install fail2ban or something similar, especially if the device is portable or you don't use ssh-keys for authentication.  Please.

If you still want to run samba, there are good reasons for this, we're here to help.

---

