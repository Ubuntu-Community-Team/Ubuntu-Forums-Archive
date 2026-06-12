---
title: "Trouble with Xbox"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by InsaniaEx on 2010-05-26
I am using a netbook (ubuntu OS) as a router for my XBox so it can connect to XBox live. I set up so auto eth0 shares with other computers. But when I try to connect to live, it stops on the XBox 360 -> Network part of the test. In more info, it tells me:
Can't obtain an IP address from your router or modem.

It was working with a Windows 7 laptop just minutes before, but I don't no longer can use this one.

Thanks for any help.

---

### Post by InsaniaEx on 2010-05-26
I really need the help now.

---

### Post by -humanaut- on 2010-05-26
So are you using wireless to connect the netbook and trying to route it with auto-eth0 (hardwired) to the xbox?

---

### Post by InsaniaEx on 2010-05-26
[http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN](http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN)

By following this tutorial, I got past the problem of connecting to network, but now I have a problem from network to internet, more info tells me problem with DNS, and i realised I had not changed the Secondary DNS. I am not exactly sure what to change it to.

---

### Post by InsaniaEx on 2010-05-26
Again, any help will be appreciated.

---

### Post by InsaniaEx on 2010-05-26
Seriously guys, I am pretty much begging here. :P

---

### Post by -humanaut- on 2010-05-26
sudo cat /proc/sys/net/ipv4/ip_forward

Post results back

---

### Post by InsaniaEx on 2010-05-26
1

---

### Post by -humanaut- on 2010-05-26
wait a second... Are you using a firewall? I looked through that article and its using IP tables if you have UFW enabled or Firestarter that's probably blocking your connection.

---

### Post by InsaniaEx on 2010-05-26
I have Firestarter installed, but I don't use it anyway. I uninstalled just incase, tried connecting to live again, no luck though.

---

### Post by -humanaut- on 2010-05-26
try sudo ufw disable 

and firestarter runs in the background i'd recommend rebooting your system and purging its config files.

also you might need to redo that entire tutorial because Firestarter could have very well rewritten your ip tables.

---

### Post by InsaniaEx on 2010-05-26
Where can I find the config files?

---

### Post by InsaniaEx on 2010-05-26
Anyone else available to help?

---

### Post by -humanaut- on 2010-05-26
locate firestarter

from a terminal.

---

### Post by InsaniaEx on 2010-05-26
Thanks, but I have to reinstall it, because for some reason I lost iptables altogether.

---

### Post by -humanaut- on 2010-05-27
Try searching synaptic for Ip Tables I really don't think Firestarter is the way to go and make sure UFW is disabled because that will set it's own rules.

---

### Post by InsaniaEx on 2010-05-27
Wait...synaptic? That the add/remove application? If so, I already have, no luck.

---

### Post by -humanaut- on 2010-05-27
Did you ever get this working? Sorry I couldn't be of more help man, I did some research into it and if you followed that tutorial word for word I can't understand why its not working I literally borrowed my sisters netbook with ubuntu remix 9.10 on it and used a PS2 to connect like the tutorial suggested and it worked.
My last suggestion would be to start over from scratch with the tutorial purge all your firewall software including IP tables reboot reinstall IP Tables then write there rules. (I manipulate UFW to manage my IP tables).

---

