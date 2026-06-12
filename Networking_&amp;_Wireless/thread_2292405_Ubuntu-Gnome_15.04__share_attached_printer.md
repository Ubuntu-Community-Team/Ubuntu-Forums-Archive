---
title: "Ubuntu-Gnome 15.04  share attached printer"
date: 2015-08-27
forum: Networking &amp; Wireless
---

### Post by RobertoRecordo on 2015-08-27
I just did a clean install after running 12.10 past EOL.

I have a printer installed, and was sharing it on my LAN. I have access the network, and can see my WD Cloud and shared folders on other computers. 

Controls/ dialogues that were on previous versions, (such as the "Share Local Printer" button in printer setup ) are not available on GNOME 15.04, I need help locating them if they are here!

I can not find any way to make a folder on this machine available on the network.
I need to share my local attached printer with other systems on my LAN, but I can not find a way to enable it.

Thanks for any help or success stories,

- Rob

---

### Post by PaulW2U on 2015-08-27
*Thread moved to **Networking & Wireless**.*

---

### Post by deadflowr on 2015-08-27
You can utilize your cups homepage to setup printer sharing.
Open any browser and type
```
localhost:631
```
in the address bar
There will be several tabs up top, one of which is administrator.
You can set access for your printers here.

If asked for a password, simply use the one you use with Ubuntu, like normal.

Hope it helps.

---

### Post by RobertoRecordo on 2015-08-27
deadflowr - thank you for the quick response. 
After seeing the site (which is unfamiliar to me) I googled to see if entering my password is a known security risk. [Christopher Negus]("https://www.google.com/search?tbo=p&tbm=bks&q=inauthor:%22Christopher+Negus%22") in the Linux Bible 2010 seems to think it is safe:D.

I don't recall doing a set up using my browser on previous installations.

Perhaps localhost is internal to my system? I unplugged my internet cable, entered my password, and discovered the program is redirecting and fails with no internet access.
 ```
http://localhost:631/admin/?OP=redirect
```

I know you are giving me good advice, and I believe it will solve my problem.
But - giving up my root password without knowing anything about _who I am giving it to_  violates all common wisdom about safe and secure computing.

Are there command line options to get this done? I am accustomed to downloading software and giving my password _to my system_ to install it.

Respectfully

-Rob

---

### Post by RobertoRecordo on 2015-08-27
I am marking this thread solved.

I found some information on using the CLI to set up a shared printer. The most useful help I found was on  was on 
[https://docs.oracle.com/cd/E26502_01/html/E29012/gllgm.html#gmflr](https://docs.oracle.com/cd/E26502_01/html/E29012/gllgm.html#gmflr)

I am not 100% sure that everything I did was necessary or useful, but I can now print from my other computers.

The difficulty was 
[LIST]
[*]find the ppd file: there are more than one on my system,  I used  /etc/cups/ppd/PSC-1400.ppd 
[*]determining the printer name for the -p option:  the GUI printer setup shows the name "PSC-1400" 
[*]finding the actual device name for the -v option 
[/LIST]
```
   
$ lpinfo -v | grep ":/"
    direct usb://HP/PSC%201400%20series?serial=CN56AB71F804BN&interface=1
    direct hp:/usb/PSC_1400_series?serial=CN56AB71F804BN
    serial serial:/dev/ttyS0?baud=115200
    network dnssd://HPOfficeJetV40xi._ipp._tcp.local/
```

Then this ran without errors

```
$ lpadmin -p PSC-1400 -E -v hp:/usb/PSC_1400_series -P /etc/cups/ppd/PSC-1400.ppd 
```

And my other computer can print - tested text file and pdf.

-Rob

---

### Post by kurt18947 on 2015-08-28
I'm not sure it would have helped your problem but I also run Ubuntu-Gnome. The included 'printers' app is pretty rudimentary. I install from the repositories "system-config-printer". I find that more informative & useful.  Good job on fixing your problem.

---

### Post by The Cog on 2015-08-28
For your info, **localhost **is normally your own system. **ping localhost** should say it's pinging 127.0.0.1 whcih is always yur own machine's loopback address.
localhost:631 will be the printer admin service on your own machine.

---

### Post by RobertoRecordo on 2015-08-29
kurt18947 - Thanks for the tip!

TheCog -

I did google and discover that it is a loop back. What alarmed me was that the program that ran did not behave in the normal expected way. Normal is that I use my administrative password to allow a program to access my system. In this case it appeared that I was handing my password to a program, and that program was attempting to use my internet connection to go to an undisclosed site for an unknown purpose.
As I said > giving up my root password without knowing anything about _who I am giving it to_  violates all common wisdom about safe and secure computing.

How would I know that it was safe?

Thanks for your interest in my problem, I invite further comments on my security worries .

-Rob

---

### Post by ODTech on 2015-08-30
In the future if you want to setup a HP printer use the package hplip. It takes alot of the guess work out of setting up a hp printer if your not experienced.

---

### Post by RobertoRecordo on 2015-09-03
Thank you , ODTech -

> **ODTech said:**
> In the future if you want to setup a HP printer use the package hplip. It takes a lot of the guess work out of setting up a hp printer if your not experienced.

So True !  I am working with a clean install and on the learning curve of using separate partitions for /home/<user> . !!! rebooting does bizarre things when two users have the same UID, but it eventually gets back to "Advanced Boot Options" and rescue is my friend. 

My printer _was_ working, but after thrashing around in /etc/passwd /etc/fstab trying to get my user accounts as I want them, I discovered
[LIST=1]
[*]my printer had become the undead, installed, identified, but useless 
[*]The most helpful, thorough, help available [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) 
[/LIST]
and yes, installing hplip and running[INDENT]```
$ sudo hp-setup
```[/INDENT]
and bob's your uncle, back in business.

Thanks for the tip!

[COLOR=#0000ff][FONT=trebuchet ms][SIZE=4]-Rob[/SIZE][/FONT][/COLOR]

---

