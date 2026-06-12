---
title: "Network and Samba Problems"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by mrxtambourineman on 2008-04-28
I just installed the new Hardy Heron i386. However, I have several problems. I am not able to access my shared folders on my XP box through the Network tab under places. If it helps, I am only able to get as far as the workgroup, but I cannot see my XP box. In contrast, I am able to see my Ubuntu box on the network through my XP box. Also, I am unable to get my printer working either. I am able to detect it when I add a printer under the SMB printer dialogue. Unfortunately, it is unable to verify and will not print the test pages. I have bi-directional support turned off. Additionally, I have my XP firewall off. Thank you for your time.

---

### Post by EarloftheWest on 2008-04-28
I'm having a similar problem.
I'm able to access my XP Pro shared drives by putting in:
smb://192.168.0.3/audio

but when I try to use places > connect to server
and enter in my computer name it won't access it. Also, I can't print to my shared printer on my XP Pro machine.

I want to use my computer name since my XP Pro machine is dynamically assigned an IP address and I just want it working the way I want.

Thanks.

---

### Post by Iowan on 2008-04-29
Search for WINS or WINBIND.  Also, "Connect to Server" frequently works better for me than "Network Places".

---

### Post by EarloftheWest on 2008-05-06
This is still a problem but I have a theory that I want to run by you.

The IP address of the XP Pro machine I want to connect to is:
192.168.68.3.

I can connect to the audio share by typing in:
smb://192.168.68.3/audio

Try as hard as I like, I can't connect to by the machine name.

smb://mshome/ is empty.

Is it possible that samba is expecting the server name to be under a different IP address, like 192.168.0.x? If so, how can I get samba to expect my IP range?

I want to connect via server name and not IP address.

Thoughts? Thanks in advance.

---

### Post by Iowan on 2008-05-08
@Earl
Short term - try adding a line to the **hosts** file with IP address and XP hostname.  Same problem as using IP address, it won't work if/when XP gets different DHCP address.

---

### Post by EarloftheWest on 2008-05-08
Iowan,

Thanks for your post.

I've told my router to assign my desktop a specific IP and I'll just access it that way in the short term.

I want to get this figured out so it works the 'right way'.

- Darren.

---

### Post by Iowan on 2008-05-08
What's in your **resolv.conf**?

---

