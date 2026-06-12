---
title: "Ubuntu Print Help"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Max'sOwner on 2009-04-27
I am trying to print on a network printer but it has a error message when i try to print. please help.

---

### Post by jimmy the saint on 2009-04-27
> I am trying to print on a network printer but it has a error message when i try to print. please help.

You are going to need to give a lot more information than that.  What is the model of the printer.  Have you installed the printer?  What is the error message?  Have you tried printing in other programs to make sure it is not an issue with that particular program? 

The more information you give us, the more likely someone will be able to help you.  Just based off the information you gave us, it could be anything from the printer being unplugged to aliens taking control of your computer! (neither are likely, don't panic!)

---

### Post by Max'sOwner on 2009-04-27
Its a HP LaserJet 4+ it does not work with ubuntu in general

---

### Post by jimmy the saint on 2009-04-27
Try going to preferences>Printing

Then add a new printer.  The process should be pretty straightforward.  I would give you a step-by-step but 
a)  I am in front of a box running Hardy and I don't know if your print dialog will be the same, and
b) the instructions should be pretty straightforward. 

 post back if you have any problems.

Edit: It should be easy because, according to the linuxprinting.org database, your printer uses the hplip driver, which is already installed for you.

---

### Post by Max'sOwner on 2009-04-27
ive done that it gives me an error message on the printer that say "invalid pers"

---

### Post by Hospadar on 2009-04-27
What happens when you ping the IP of the printer, does it show up?

---

### Post by Max'sOwner on 2009-04-27
> **Hospadar said:**
> What happens when you ping the IP of the printer, does it show up?
ummmmm dont undestand please clarify

---

### Post by Max'sOwner on 2009-04-27
Here's more detail, if you can help a newbie:

I have an HP LaserJet 4 in the LPT1 of a computer on my windows network.  It's my main printer.  It is seen by Ubuntu.  When I print, the job fails.  When I watch the windows print monitor, interestingly, the print job appears, then seems to be automatically deleted.  The error code appears on the printer, that suggests that we have some sort of "permission error".  

Not sure what causes this.  Might Ubuntu have a separate authorization/authentication/password requirement with the printer? 

Thank you

---

### Post by jimmy the saint on 2009-04-27
It would seem that the issue is on the windows machine.  I didn't realize that you were sharing it via a windows box. 

in order to ping the box, open your terminal appliations>accessories>Terminal

and type in 
[code]ping <printer_ip_address>[/code/]
where <printer_ip_address> is the ip address of your printer.  I don't know how that would work since it is shared through your windows box.  I wish I could be of more help, but someone that knows more about windows print sharing will have to step in on this one.  My printer is plugged directly into the router, so I have never had to deal with that.

Good Luck!

---

