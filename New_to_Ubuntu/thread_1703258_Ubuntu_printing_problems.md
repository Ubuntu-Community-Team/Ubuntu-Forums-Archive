---
title: "Ubuntu printing problems"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by IKT-kr on 2011-03-09
Hello!

I work in the Internal IT Systems department at my workplace. We keep the Windows machines running and give support. But now, we got a problem. Recently, people using Ubuntu (what operating system people want to use, is vouluntary) can't print in the A4 sheets.

Here's the details:

1. One day, (can't remember the date) one of the Ubuntu users contacted me. No matter what he chose under printer properties or printer preferences etc. the document would always be printed in the A3 format. He had tried everything, like installing a new driver, rebooting both his computer and the actual printer. 

2. I'm not an Ubuntu expert and have always used Windows. My computer (with Windows) prints perfectly and I can decide for myself what format I want to use when printing. Both A4 and A3 sheets worked fine.

3. I removed the A3 possibilty from the printer and configured it to only use A4 all the way. The problem now, is that the Ubuntu users can't print at all.

Does anyone have any ideas on how to help me? I'd be very happy for answers! Thank you for your time!

---

### Post by Sef on 2011-03-09
1) Moved to ABT.

2) What printer do you have?

3) Was any changes made any where on the printing system? (desktop computer, server, other device/part)

---

### Post by IKT-kr on 2011-03-09
> **Sef said:**
> 1) Moved to ABT.

2) What printer do you have?

3) Was any changes made any where on the printing system? (desktop computer, server, other device/part)

Reply to 2. Sorry, I forgot to mention that. It's a Canon                      iR C2380

Reply to 3. No, we've made no changes. It just stopped working all of a sudden. At least, no one has admitted they have done anyting on the printer. 

The problem is there for all the Ubuntu users, so I don't think that it can be that one person installed the wrong driver or someting like that.

---

### Post by Sef on 2011-03-09
> Reply to 3. No, we've made no changes. It just stopped working all of a sudden. At least, no one has admitted they have done anyting on the printer. 

The problem is there for all the Ubuntu users, so I don't think that it can be that one person installed the wrong driver or someting like that.

Are they connected to the printer though a print server? Since everyone using Ubuntu has problems and Windows does not, I would suspect that would be the problem, or something with the printer software is not working well.

---

### Post by IKT-kr on 2011-03-09
No, we're not using a print server. The user adds the printers that convinent for him or her to use locally him-/herself.

---

### Post by Sef on 2011-03-09
> No, we're not using a print server. The user adds the printers that convinent for him or her to use locally him-/herself.

1) Try another printer and see if the same result happens. If it does, then problem would most likely lie in the connection to the printers. (It would highly unlikely that all the computers would have this problem at the same time.)

2) Switch with a printer that works and see if the problem is with the new installed printer.  If it works, then the problem lies with the original printer. If it does not, and the original printer works at a new place, then I would suspect a network problem. 

3)How do the printers connect to the printer (IP address, or what other way)?

In brief:

Canon and other printer switched:

Both Work - network problem

Canon works; other printer does not - network problem

Canon does not work; other printer works - Canon problem

Both do not work - network problem and canon problem

---

### Post by IKT-kr on 2011-03-10
Hello again!

One guy reinstalled Ubuntu from scratch and everything works perfectly for him now. Do you have any idea why? Can it be that he's got a new driver? I can't that make sense since the other ones also have tried several drivers for the printer...

Do you think there's any quick way to fix the problem? I fear it could be quite unpopular to tell everyone they have to reinstall their beloved operating system.

---

### Post by IKT-kr on 2011-03-10
> **IKT-kr said:**
> 
One guy reinstalled Ubuntu from scratch and everything works perfectly for him now. 

A little misunderstanding. He tried to print from Windows. He can't print from Ubuntu. At least now we know that a reinstallation does not help, right?

Reply to your 1: The Ubuntu users can print at will at all the other printers. But they think it's to far to walk.

Reply to your 2: If i understood your post correctly, you wanted a me to set up a new printer at the same place as the one I'm trying to fix. That's quite difficult. All our printers are huge and heavy... so I won't be able to move them.

Reply to your 3: Yes, we connect to them over the network via IP addresses.

---

### Post by Sef on 2011-03-11
> Reply to your 2: If i understood your post correctly, you wanted a me to set up a new printer at the same place as the one I'm trying to fix. That's quite difficult. All our printers are huge and heavy... so I won't be able to move them.

Reply to your 3: Yes, we connect to them over the network via IP addresses.

1) Since the Ubuntu computers can print to other printers, I have some questions/suggestions:

a) Does the printer have a static IP address? If so, are they the same?

b) If it uses a dynamic address, set a static IP address.

c) Do you have same printer elsewhere that can print to Ubuntu? Check the settings on that and make sure the nonworking one has the same settings.

d) Has the printer driver been updated recently or has cups been updated recently?

---

### Post by IKT-kr on 2011-03-11
A + B) Yes, the printer has a static IP address. It has not been changed. And there is no IP address conflict either.

C) Yes, we have an identical printer that the printing for Ubuntu users works perfectly... but they don't want the extra exercise and running up the stairs to the next floor.

D) Nobody made any changes. It seems like the printer didn't want to be friends with the Ubuntu boys, all of a sudden.

---

### Post by Sef on 2011-03-11
1) The only thing I can think of is to check the settings on the good printer and check that the settings are the same on the nonworking printer.

2) Other Ubuntu places to ask:

a) IRC
b) launchpad

---

### Post by IKT-kr on 2011-03-14
1) It seemed like it they're the same a few days ago, but I'll check it again.

---

### Post by zondfive on 2011-03-26
> **Sef said:**
> 1) Moved to ABT.

2) What printer do you have?

3) Was any changes made any where on the printing system? (desktop computer, server, other device/part)


Please note that not everyone here knows what ABT is..

---

### Post by goldblattster on 2011-03-26
> **zondfive said:**
> Please note that not everyone here knows what ABT is..

It means Absolute Beginner Talk, obviously.

---

### Post by IKT-kr on 2011-03-28
> **goldblattster said:**
> It means Absolute Beginner Talk, obviously.

That's obvious for Captain Windows.

---

