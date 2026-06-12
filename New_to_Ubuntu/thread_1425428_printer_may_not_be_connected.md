---
title: "printer may not be connected"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by ginestre on 2010-03-09
After accepting the latest routine security upgrade to CUPS, I now get a message every time I try to print: 'Printer may not be connected.'

But of course the printer *is* conncted- I can browse to its web interface and print a test page. But I can no longer print anything useful, since it now takes upwards of an hour to 'process' documents in the CUPS queue, on those rare occasions when it doesn't just fail completely.

What should I check?

TIA

---

### Post by Scunnered on 2010-03-09
Like you I posted against this heading in April 2009.  If I knew how to identify the post or set a link to it I would give it to you.

Can I suggest you try [http://www.googlubuntu.com/](http://www.googlubuntu.com/) as this can be a better for results than the forum search.  Suggest you show (SOLVED) before text 

Sorry I can't be of more assistance

---

### Post by Robster2 on 2010-03-09
> **Scunnered said:**
> Like you I posted against this heading in April 2009.  If I knew how to identify the post or set a link to it I would give it to you.

Can I suggest you try [http://www.googlubuntu.com/](http://www.googlubuntu.com/) as this can be a better for results than the forum search.  Suggest you show (SOLVED) before text 

Sorry I can't be of more assistance

I think he referring to: 

[http://ubuntuforums.org/showthread.php?t=1011612](http://ubuntuforums.org/showthread.php?t=1011612)

---

### Post by Scunnered on 2010-03-09
This was the post that I was referring to [http://ubuntuforums.org/showthread.php?t=1134997](http://ubuntuforums.org/showthread.php?t=1134997) that resolved my problem.

If you had followed my google suggestion you would have seen that there were many similar posts over the years.  This seems to be a recurring problem.

Trust you can resolve matters now

---

### Post by dorothykinder on 2010-03-09
I had a similar kind of problem with my printer when i was connected to Windows OS, i could be able to make a print out of the test page but could not print any other documents. 

I later disabled the entire software and then again reloaded it and then it was all working fine.

---

### Post by Mel Thompson on 2010-07-11
System > Administration > Printing

Then wait for icon of desired printer to show in dialog box.
In my case, the printer is the HP 1012.

Then go to menus above, (after selecting printer icon).

Printer > Properties

Then, on the side, are options like "Settings, Policies, Access Control."

When the dialog box opens, "Settings" is the one already highlighted,
so leave it there.

There is a line of text on the page that reads "Device URI."
Across from it is a button that says "Change."  Click it.

The printers will appear.  Highlight the desired one.  In my case,
I only have one printer, the HP 1012.

Down toward the bottom of the page an odd "+" sign appears.
It turns out to be a button which is the "Connection" button.  Click it.

Toward the bottom of the page an HPLIP option appears, and is highlighted
by default.  Instead, highlight the "USB" option.  Then press "Apply."

That will actually solve the problem for most HP printers.

My prayers go out to the newbies.

---

### Post by mk04 on 2010-07-12
> **Mel Thompson said:**
> System > Administration > Printing

Then wait for icon of desired printer to show in dialog box.
In my case, the printer is the HP 1012.

Then go to menus above, (after selecting printer icon).

Printer > Properties

Then, on the side, are options like "Settings, Policies, Access Control."

When the dialog box opens, "Settings" is the one already highlighted,
so leave it there.

There is a line of text on the page that reads "Device URI."
Across from it is a button that says "Change."  Click it.

The printers will appear.  Highlight the desired one.  In my case,
I only have one printer, the HP 1012.

Down toward the bottom of the page an odd "+" sign appears.
It turns out to be a button which is the "Connection" button.  Click it.

Toward the bottom of the page an HPLIP option appears, and is highlighted
by default.  Instead, highlight the "USB" option.  Then press "Apply."

That will actually solve the problem for most HP printers.

My prayers go out to the newbies.


This fixed my problem perfectly!! Thanks so much. :p

---

### Post by Georgia boy on 2010-07-13
Somehow I did the apply for the USB connection so I'm able to print. But now I'm not able to scan. If you view my thread on Simple Scan not working you can see I've been trying various things to do so. Just can't get scan to work. It just don't see the connection. 

Tom

---

