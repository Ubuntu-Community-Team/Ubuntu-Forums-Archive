---
title: "getting a lexmark x4650 to print wirelessly"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by charlieluna on 2011-02-20
Ok guys. I have to say that I have read several posts, and they helped me tremendously. kudos to all linux programmers/nerds, you helped me change the administrator password so i could actually get the driver for my printer installed. now, i need help getting it to print wirelessly. i read another thread that helped me print out a page with all network information on it. so all i need is a little help with the wireless part and i am good to go. thanks to all of the linux community!! you have helped me get away from the corporate monopoly that microsoft is!!!

some more information about this printer. it is wifi connected to our router. when any of us send a print job to it, the job gets sent through our internet router and then wirelessly to the printer. then it spits out the document. it is not connected to any computer at all. just the wall socket for power. HELP!! this is the last step for me to be completely away from windows!

---

### Post by cariboo on 2011-02-20
Can you ping the printer eg:

```
ping <printer_ip_address>
```

If you can ping it you should be able to set it up as a network printer. Go to System->Administration->Printing, click Add printer, then click Network Printer->Find Network printer, and input the printer ip address, then it's just a matter of following the prompts from there.

Note: if you aren't sure what the printer ip address is, you can use nmap to find it, open a terminal and type:

```
sudo nmap -sP 192.168.1.0/24
```

If you don't have nmap installed, you will be prompted to install it, and what command to use. You may have to change the netblock ip address to whatever you are using. My networked Brother printer shows up like this:

```
Nmap scan report for 192.168.1.230
Host is up (0.00076s latency).
MAC Address: 00:80:77:89:A3:29 (Brother Industries)
```

---

### Post by charlieluna on 2011-02-20
i pinged it. but it looks like it wasn't going to stop pinging. so i closed the terminal. when i try the other way you mentioned, it goes all the way to asking to print a test page but it comes up with an error. i am using the i386 driver instead of a full fledged 64 bit driver. it installed ok but it just won't allow me to print. anymore suggestions would be great. 

i know the address of the printer but i just can't seem to get it right.

do i need something called cups to use this printer?

---

### Post by charlieluna on 2011-02-22
I solved my problem!! WOOHOO!! I can now make the final switch! No more windows for me!! this is how i did it.

1. First thing i did was to change the administrator password to something i know. I opened a terminal and used "sudo passwd" and it was really easy.

2. Once that was done, I downloaded the driver from lexmark. I ran it, put in the admin password, and followed the instructions even up to the point of connecting the printer to my laptop via usb cable. but this doesn't mean that will need to be hooked up to print. 

3. I unhooked my laptop. and then proceeded with the next phase.

4. this next phase requires you to be at the printer. on the control panel, push the setup button. arrow over to find the network setup option. press ok.

5. arrow over to find TCP/IP. push ok. 

6. arrow over to find IP address. press ok. this will give you the ip address of the printer. write it down.

7. go back to your laptop and click on system. highlight administration and then click printing in the menu.

8. in the new window, click on server. highlight new and then click on printer.

9. in the new window, click network printer. then click find network printer. 

10. on the right side, put the ip address in the text box for host. click find. it should find it and download the driver. i know, you might be thinking redundant but it is necessary. i tried it without downloading the driver first and it wasn't in the list of models you can choose from. after i downloaded the driver from lexmark and went through this process again, the model was there. 

11. it should pull up a list of manufacturers now and you can choose lexmark. then choose the 3600-4600 model since the x4650 belongs in that category. 

12. it will display a few names for your pc and the printer and just keep clicking forward and it will be done eventually. 

13. you should be able to print wirelessly now. 

good luck and enjoy!!

---

