---
title: "Net configuration problem using PPPoE / RP-PPPoE"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by amogh8188 on 2008-06-03
Guys, i am nt able to configure my net in Ubuntu Linux.

earlier thru my LAN, there was a single service provider, so all my PPPoE requests went directly to him ... but now my provider is an external one ...

In Windows i get a list of service providers to select from .. while in Linux there is no option of getting the list ... my request goes to the default one which is nt my provider, he just provides the LAN for me ..

Plz guys help and guide me ..



Also i used the default pppoe package ... plz tell me how to install the RP-PPPoE package which i have downloaded thru Windows ...

---

### Post by superprash2003 on 2008-06-03
if its a DSL connection.. then type sudo pppoeconf in the terminal and set it up

---

### Post by amogh8188 on 2008-06-03
No, its not a DSL connection. Its through LAN Card.

---

### Post by amogh8188 on 2008-06-03
Well guys i managed to setup the connection using these instructions

[I]I have seen many people having a hard time setting up PPPoE on ubuntu and I have decided to write a simple guide towards it.

There is an inbuilt tool in ubuntu called pppoeconf which helps us to setup our PPPoE. To use this, open Terminal and write 'sudo pppoeconf' and follow the instructions. In case this does not work or you use an access concentrator, use the following method...

1) Go to System --> Administration --> Synaptic Package Manager
2) Check whether build-essential package is installed. If it is not, install it using the ubuntu CD/DVD.
3) Since you do not have internet access on ubuntu, use your alternate OS or your friend's PC to download [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)

4) Open it with ubuntu's archive manager and extract the folder within to your desktop
5) There will be a file within the folder known as ./go. Open Applications --> Accessories --> Terminal. Write sudo and drag and drop the file in the terminal and press enter. If all goes well RP-PPPoE would be installed successfully.
Provide all the details RP-PPPoE setup requires.

6) Type sudo pppoe-start in the terminal to bring up the connection and sudo pppoe-stop to shut the connection.
7) If you want to bring up the connection at boot time, you will have to edit the rc.local file. Open the Terminal and type sudo gedit /etc/rc.local. Insert the line pppoe-start just before exit and save the file. Done.

Note: If your ISP requires an access concentrator and a service name, you will have to edit the pppoe.conf file in the following manner.

Type this in the terminal...
'sudo pppoe -A'
Note down your desired Access Concentrator and Service Name.

Then
'sudo gedit /etc/ppp/pppoe.conf'
There you will find ACNAME= and SERVICENAME=
Edit them as per your requirement. Save and exit.[/I]


These were taken from some forum and helped me a lot.

But the problem is the connection starts, but i am not able to open any page in the browser.

---

### Post by amogh8188 on 2008-06-03
Thanks guys for ur help. The problem is solved.

---

### Post by xPirate on 2008-11-04
> **amogh8188 said:**
> thanks guys for ur help. The problem is solved.

how?

---

