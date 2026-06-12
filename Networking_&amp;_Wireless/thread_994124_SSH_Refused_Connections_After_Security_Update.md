---
title: "SSH Refused Connections After Security Update"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by GenuineXP on 2008-11-26
I'm running a server with Ubuntu Hardy nearby to my school. Since it's Thanksgiving break, I'm hundreds of miles away and don't have physical access to it. I read about a serious SSH bug that affected my server, and decided to update (I thought there would be some risk in this, but the [bug]("http://www.ubuntu.com/usn/USN-612-2") seemed pretty serious).

Anyway, the update seemed to work, and I got an ncurses screen asking about checking for vulnerable keys. Well, in typical fashion, it took me too long to actually respond, and the hanging connection failed. My virtual terminal just sat there, and no matter what I pressed, nothing happened. Before closing that terminal, I opened another and tried to connect to my server, but I kept getting a message saying it (the server's IP, actually) closed the connection.

So... now what? Is there any way I can get SSH working remotely, or am I screwed? Also, if SSH is TCP-based, then why do I (too) often lose connectivity? I find that if I don't enter any input into a remote terminal for about five minutes, it "dies", and I have to reconnect. Is there a good reason for this?

Thanks.

---

### Post by sammy_pal on 2008-11-27
If your key was in the blacklist of vulnerable keys, then it might be that the openssh server is no longer allowing you to use the blacklisted key. Anyway if you had not disabled password based authentication previously, then you should be able to login using your password, if that is the case.

---

### Post by GenuineXP on 2008-11-29
Hm, I did not disable password-based authentication. Then again, I didn't explicitly enable it either. Is it enabled by default?

If SSH continues to refuse my connections, will I have to log in on the physical machine to fix this? Because I can't remotely connect, I've been unable to try resetting the machine, which is probably what I'll try as soon as I get physical access to it again. Do you think this could allow me to connect?

Also, as I mentioned previously, does anybody else experience SSH connections that die if idle for a few minutes or more? Is there any reason specific to SSH that this happens, or is it just an unreliable route or something going on with the network I'm connecting through?

Thanks for the help.

---

### Post by sammy_pal on 2008-11-29
Yes, password authentication is enabled by default. You can try to logging in by using ```
ssh -l username ServerIP
```This should ask for your password.
By the way, just to ensure that everything else is alright, can you ping your server? I once experienced a somewhat similar problem while updating a remote server. A new kernel version was available and the kernel got updated. After trying to reboot remotely, the machine didn't come up and was not accepting any ssh connection. I could not even ping it. Later on I found that the machine just hung up after loading the new kernel, and due to some ACPI issue the boot process didn't complete successfully. I had to reset the server and make it load the old kernel by editing the grub. In my case it was not so much of a trouble, as the server is located at an adjacent building, I could reach there in just 10min to figure what was wrong.
Secondly ssh sessions, if idle are often terminated by the sshd. To avoid this use the option "-o ServerAliveInterval=50" while logging in, i.e use
```
ssh -o ServerAliveInterval=50 -l username ServerIP
```This will send a keepalive packet to the server every 50sec. You can change the interval. This prevents the server from hanging up.
Finally, if the machine doesn't allow you to login using ssh, then I think the only option to check what is wrong, is by physically logging in.

---

### Post by GenuineXP on 2008-11-30
Wow, I finally got this sorted out after a lot of hassle.

I just got back home (where the server is) and tried to log in to the physical machine, but the added graphics card is not being enabled by the BIOS (I think in favor for the on-board graphics), and I don't have an old D-Shell cable laying around. So... no physical access either!

In the end, I realized that I had previously installed the webmin package! While it it configured to refuse connections from the Internet, I was able to log in as root from my LAN. From there, I use the web-based shell to do some snooping. It turns out that dpkg got confused in needed to be fixed after that SSH session was disconnected during the upgrade. So, I ran the appropriate command, followed by some SSH key checks.

Bingo! Now everything's up to date and I can finally connect again (after flushing the old keys from all clients). Thank goodness for Webmin!

Thanks for all of the help. I'll definitely be using the ServerAliveInterval option from now on, especially when performing administrative tasks.

---

