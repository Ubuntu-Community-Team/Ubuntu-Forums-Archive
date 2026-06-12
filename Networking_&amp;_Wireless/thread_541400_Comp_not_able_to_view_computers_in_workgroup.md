---
title: "Comp not able to view computers in workgroup"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by Jasonmrc on 2007-09-02
I'm on Ubuntu 7.04 and I can't access my windows network.
When I go to Places > Network > Windows Network I don't see anything, not even myself. I've configured the workgroup in smb.conf but it still doesn't work.

Also, the windows computers cannot see this computer.

From what i've read around the forums it seems that this is a common problem. Does anyone have an answer?

---

### Post by unimatrix on 2007-09-03
Same problem, only other Windows and Linux computers can see this machine.

I can though access other computers through, for example smb://192.168.2.xx
(also smb://machinename - after i've configured the /etc/hosts file)

---

### Post by nickmcg on 2007-09-03
Have you installed winbind?
This gives access to the netbios names, and should help.

You will also need to edit /etc/nsswitch.conf to add 'wins' (without the quotes) to the line beginning 'hosts:'

HTH

Nick

---

### Post by carroll on 2007-09-03
> **nickmcg said:**
> Have you installed winbind?
This gives access to the netbios names, and should help.

You will also need to edit /etc/nsswitch.conf to add 'wins' (without the quotes) to the line beginning 'hosts:'

HTH

Nick

Where do I get Winbind?  I didn't seem to find it anywhere on the Ubuntu net

---

### Post by unimatrix on 2007-09-03
OK I've solved the problem.
The firewall on my client machine was blocking a service called *Sun's RPC portmap* (port 32783). I have no idea how this is relevant, but now suddenly everything works. I can see all the computers when I go to network:/// and even the wins server is giving me names so I don't need them in /etc/hosts.

Hope this helps anyone.

---

### Post by nickmcg on 2007-09-03
> **carroll said:**
> Where do I get Winbind?  I didn't seem to find it anywhere on the Ubuntu net

Either from synaptic or ```
sudo apt-get install winbind
```

Nick

---

### Post by michaelzap on 2007-09-03
Aha! I have just been shutting Firestarter down in order to get a directory list of local shares, but I hadn't bothered to figure out exactly what was the specific issue. This is something that should probably be more widely known, since I've seen several posts on it.

---

### Post by unimatrix on 2007-09-03
Update: It's not just the port I've referred to before. I had to open all ports from 32770 to 32900 as they are random every time I reboot.

---

### Post by carroll on 2007-09-04
Nick I appreciate the response.  Unfortunately I am a brand new user of Ubuntu and have no idea how to use your code.  Also, I looked on Synaptic website and did not find any winbind program there.  Please help further.

---

### Post by carroll on 2007-09-04
Dumb me.  I found Synaptic and installed Windbind, but I don't know how to edit /etc/nsswitch.conf.  When I try I get the message that I do not have permission to write into /etc.  Can you guide me here.

---

### Post by nickmcg on 2007-09-05
> **carroll said:**
> Dumb me.  I found Synaptic and installed Windbind, but I don't know how to edit /etc/nsswitch.conf.  When I try I get the message that I do not have permission to write into /etc.  Can you guide me here.


Sorry about that.

If you need to execute code, then the easiest way is from terminal.
Applications->Accessories->Terminal

Then type in ```
sudo gedit /etc/nsswitch.conf
```
 entering your password when prompted. This will allow you to edit the file.

FYI 'sudo' (or gksudo) makes you an administrator so you have extra rights - this means that you won't accidentally foul things up as your usual logon.:)

HTH

Nick

---

### Post by gjb3129 on 2007-09-13
Have you tried manually configuring your network.

System>Administration>Network

Wireless LAN select the 

Wireless Connection (wlan0)
Wireless Connection (wmaster0)

and click on properties.  (You will have to do this one at a time, obviously)

Click on "Enable Roaming Mode" to **Disable** it.

Click on "Network name (ESSID)" and either type in the SSID from your wireless router, or select it from the list if it is already in the drop down menu.  

If your network has a password, select "Password Type" and then type the password in the "Password" field (although if you had to do this already, you are probably already seeing the other computers), else leave the "Password" blank

Finally, in the Connection settings->Configuration field either choose "Automatic Configuration (DHCP)" if the server automatically assigns IP addresses (usually the default) or "Static IP" and fill in the rest of the fields with the IP addresses that you got from your network administrator.

If you want to save these settings just select Save (Disk Icon) next to the Locations Field and enter the desired location name.  This will make it easier to jump between networks.

Hope this helps.

---

