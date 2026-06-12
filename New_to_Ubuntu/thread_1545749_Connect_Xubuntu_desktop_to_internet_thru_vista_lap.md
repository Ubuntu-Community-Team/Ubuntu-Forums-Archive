---
title: "Connect Xubuntu desktop to internet thru vista laptop"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by darkeale on 2010-08-04
Hi,

I have an old desktop computer which doesn't have a wireless card, so I am wondering if I connect it to my vista laptop with a router, can i then connect to the internet on the desktop using my laptops wireless internet connection?  So basically sharing the internet connection between the 2 computers?

Thanks
Alex

---

### Post by TTGRULES on 2010-08-04
Well... ive done it with xp... but vista's network manager is different... im going to run some tests real quick and see what you need to do.. you shouldn't have to mess with anything on the ubuntu side.. just the vista computer...

---

### Post by TTGRULES on 2010-08-04
turns out that the method is very similar on a vista pc... 

I tried it on one computer.. but the results might vary for different machines.... Be very careful about changing stuff... write down configurations so that you can change them back if it doesn't work or something...


Open the network connection manager..

select the wifi connection and open its properties dialogue

click on the sharing tab and enable sharing...

if you want, disable the little thing that says "let other computers have the ability to modify or disable this" or something like that...

then apply and close that properties dialogue....

open the properties dialogue on the wired connection... 

select ipv4  (tcp/something else) and click the properties button...

if needed, change the ip address to say 192.168.0.1

don't mess with the mask address

then select *use the following dhcp host... and type in 192.168.1.1 or the address of your wifi router.... 

plug a cable inbetween the two computers and you should be good to go....



If that doesn't work, you can always try bridging connections.. but that makes it where the vista PC can't access the internet while the bridge is in place... I tried it before I found this method a while ago....

---

### Post by darkeale on 2010-08-04
"then select *use the following dhcp host... and type in 192.168.1.1 or the address of your wifi router.... "

2 things, I don't have the option for "use the following dhcp host" in the properties for the wired connection.  Also, how do I check the address for my router.

Many thanks,
Alex

---

### Post by TTGRULES on 2010-08-04
sorry... its DNS... not DCHP....  to get to it, open the connection properties, select ipv4 tcp and then hit properties... unless someone changed it, your router ip should be 192.168.1.1      
you can test it by entering the ip into your browser... it should ask you for a username and password if it is the router...

---

### Post by darkeale on 2010-08-04
Ok, I now have the correct IP for the wireless.  Thanks!
Still no internet though.  I have used a router to join the 2 computers together with cables.  Will this affect things?
Also, when in the box when I tick "Share the internet connection" in the properties for the wireless, do I have to tick any of the boxes that come up when clicking the settings button on that screen?

Many thanks for your help,
Alex

---

### Post by TTGRULES on 2010-08-04
yes... you actually don't need the router.. just connecting them with a simple ethernet cable should suffice.. if you still have no internet connection, i will be very supprised. I completed the same steps on a vista computer I happened to have available with wifi and it worked fine, but computer configurations are always different... let me know how it works out!

---

### Post by darkeale on 2010-08-05
Hi,

I tried with just an ethernet cable, and nothing happened.  Neither of the green lights on the ethernet slots on the back of the computers came on.  I have been told I need a crossover cable for the computers to be able to communicate with each other, so I am going to buy one today.
After I have tried that I will let you know how I get on.

Many thanks for your help,
Alex

---

### Post by darkeale on 2010-08-05
I have just got the crossover adapter, and everything works perfectly. 

Thanks so much for your help!
Alex

---

