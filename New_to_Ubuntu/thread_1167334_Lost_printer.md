---
title: "Lost printer"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Tighearna on 2009-05-22
I upgraded to jaunty, now my printer doesn't work. I'm using an HP Officejet Pro L7680 all in one. It worked fine before the upgrade, and the device manager seems to be working fine.

But when you try to submit a print job, the acknowledgement dialog shows the printer but it is greyed out and it doesn't give you the option to print.

I'm not sure if this is my system or jaunty, I searched and didn't see anything regarding this I assume it's me.

Thank you,
Jim

---

### Post by taurus on 2009-05-22
Can you just remove it and reconfigure it again from System -> Administration -> Printing -> New?

---

### Post by mechdave on 2009-05-22
I always prefer to use the web page config, firstly make sure that cups is running by typing into a terminal ```
 sudo /etc/init.d/cups status
```
If cups is not running then start it by typing into a terminal ```
sudo /etc/init.d/cups start
```
Then open up firefox and type into the address bar ```
127.0.0.1:631
```
That will take you to the cups web admin page, you can administer all your printers from there including add and remove them. If you are asked for a username/password combination, use your own account username and password.

---

### Post by khelben1979 on 2009-05-22
The recommended driver is explained [here]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_Pro_L7680") if you need it (OpenPrinting database).

---

### Post by Tighearna on 2009-05-22
I appologize for posting a question and then disappearing. I got called away as soon as I had posted that.

I accessed the cups control page via firefox removed the printer and reinstalled it.

Worked like a charm.

Thank you all

Jim

---

### Post by Hoary on 2009-06-28
I'm in a different but related predicament. Very simply, my little 8.04 machine was happily printing to its Brother HL5270DN (connected directly via USB) till the day before yesterday, and I haven't consciously made any change since; but now whenever I want to print I'm only offered the option of "generic printer" and any attempt to use that brings a curt error message. A look in System|Administration|Printing tells me *CUPS server error / The CUPS scheduler is not running*.

The advice in this thread (though for a later version than 8.04) looked promising. I thought I'd try it, and IFF still lost then post my own question. Here's what I (perhaps ignorantly) thought was the key:

> **mechdave said:**
> I always prefer to use the web page config, firstly make sure that cups is running by typing into a terminal ```
 sudo /etc/init.d/cups status
```


I don't even have /etc/init.d/cups (I looked with GNOME commander and ls). The only item named cup* in that directory is cupsys (whatever that might be). 

What to do? Thank you for any help. (I'm not an absolute beginner but NB I'm not far off.)

PS: [answers.launchpad.net/ubuntu/+question/22028]("https://answers.launchpad.net/ubuntu/+question/22028") tells me the answer to my question: *sudo /etc/init.d/cupsys restart*

---

