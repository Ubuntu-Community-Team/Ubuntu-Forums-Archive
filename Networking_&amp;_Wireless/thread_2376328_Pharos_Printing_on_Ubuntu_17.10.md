---
title: "Pharos Printing on Ubuntu 17.10"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by jj4884 on 2017-11-01
To all that may flag this as repeated.... All solutions I googled for and browsed on the forum are either unanswered or old/outdated.

I am trying to configure my University's Pharos printers. I want to print from my Linux laptop so I don't have to wait in line for a library/lab computer in order to print a page. I am currently using Ubuntu MATE 17.10, but this solution could be possible for other variants. The School IT department does not want to help since they see Linux as "low priority".  I am trying to help my fellow IT/CS students who may run linux on their laptops as well.

I know that I have the correct URL and that sending prints is communicating with the server, but the print jobs do not end up in my queue. I cannot figure this out. I tried the python solution, but no luck.

IS it possible for someone to request a Snap package of the Pharos Popup client? I cannot seem to get a feedback line to the company, but it seems to be something that should be pursued in the future.

---

### Post by coldraven on 2017-11-02
I really don't know about network printers but out of interest I dug out some info.
From the Pharos site here: [https://community.pharos.com/thread/1263](https://community.pharos.com/thread/1263)
> 
**Background**
LPR/LPD is a TCP/IP application  that transmits a print job from a client to a print device. LPR means  "Line Printer Request" and is the client-side component of the  transmission, and LPD, or "Line Printer Daemon" is the server-side (in  this case, printer-side) component. By default, this communication  occurs over TCP port 515. Microsoft has supported LPR/LPD beginning with  Windows NT 3.51, is native to all Unix/Linux systems, and is supported  by CUPS in MacOS X and Linux variants.

Then in Ubuntu I looked at the "Add Printer" options, under "Select Device> Network Printer" you can choose LPD/LPR Host or Printer.
Presumably you then have to enter the Host and Queue parameters. It seems that knowing the Queue name is important. See attachment
At the bottom of the linked page someone has posted a DOS bat file that tests the printer, maybe someone here can translate it into a bash script.

---

### Post by jj4884 on 2017-11-02
The Pharos queue is tied to my Active Directory Username.

---

### Post by coldraven on 2017-11-03
> **jj4884 said:**
> The Pharos queue is tied to my Active Directory Username.
For a better chance of a solution more info would be good. Like what printers/setting etc. that you have already tried.

---

### Post by jj4884 on 2017-11-03
All directions I've seen online say use Generic Printer. I know we use many different models of printer across campus. The popup only requires Username and a "name" for your document. You then go to the cardreader with your id and swipe you card/enter your ID#. Then the documents show up in the queue. But there does not seem to be a way for communication with the card reader.

---

### Post by coldraven on 2017-11-04
> **jj4884 said:**
> All directions I've seen online say use Generic Printer. I know we use many different models of printer across campus. The popup only requires Username and a "name" for your document. You then go to the cardreader with your id and swipe you card/enter your ID#. Then the documents show up in the queue. But there does not seem to be a way for communication with the card reader.
I'm confused, in your first post you talked of getting a snap package and now you mention the "pop-up". 
So have you managed to get a Pop-up client for Linux, if so how?

My second question: Is this the "Python solution" that you mentioned in your first post?
[https://github.com/junaidali/pharos-linux](https://github.com/junaidali/pharos-linux)

---

### Post by jj4884 on 2017-11-20
That is the python solution I was referring to. 

However, most documentation on the subject of Pharos printer configuration appears to be proprietary to each college campus the documentation comes from. I tried installing the Python solution with no success.

---

