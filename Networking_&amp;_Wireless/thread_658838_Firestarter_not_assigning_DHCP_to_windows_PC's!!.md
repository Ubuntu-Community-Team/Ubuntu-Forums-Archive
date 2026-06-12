---
title: "Firestarter not assigning DHCP to windows PC's!!"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by bazzieb on 2008-01-05
I used to have firestarter installed and working 100%. I like it cause it was easy to setup and get working. My HDD crashed and i re-installed UBUNTU 7.10 and for some reason firestarter just doesnt want to assign addresses to my MS PC's. Firestarter doesnt seem to give me any errors. PLEASE HELP!!

---

### Post by foolsh on 2008-01-05
I never could firestarter to do that by itself either but I install dhcp3-server and configured to do the job.  just edit the /etc/defualts/dhcp3-server and /etc/dhcp3/dhcpd.conf file to your whims.

---

### Post by Predator[23rd] on 2008-01-05
[http://www.fs-security.com/docs/dhcp.php](http://www.fs-security.com/docs/dhcp.php)

> Note: Firestarter does not itself include a DHCP server, it depends on the underlying system to provide this feature. The system does not need to have the DHCP server configured, or running. It is sufficient that the dhcpd program is located on the system, after that Firestarter will manage the DHCP server completely on the user's behalf.

---

### Post by bazzieb on 2008-01-05
could you please give an example of what those two files should look like once configured?? Thanks:KS

---

### Post by Predator[23rd] on 2008-01-05
do the following for Firestarter to handle your DHCP server 

1° **sudo apt-get install dhcp3-server**

2° start Firestarter, EDIT > PREFERENCES > check ENABLE DHCP FOR THE LOCAL NETWORK

3° edit DHCP SERVER DETAILS as needed

done!

---

### Post by bazzieb on 2008-01-05
I have done that, thanks but i get an error msg. Firestarter failed to start. An unknown error occurred. Any suggestions:confused:??

---

### Post by Predator[23rd] on 2008-01-05
does firestarter totally fail to start?

try removing and reinstalling firestarter.

---

### Post by bazzieb on 2008-01-06
I tried but it didnt work. I am gonna try to get the DHCP working from dhcp3-server or dnsmasq and then just use firestarter for connection sharing. Will keep posting if i sort it out.:KS

---

