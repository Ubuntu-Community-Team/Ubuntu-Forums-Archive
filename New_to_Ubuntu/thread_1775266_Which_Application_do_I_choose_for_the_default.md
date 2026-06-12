---
title: "Which Application do I choose for the default??"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by TAspr on 2011-06-04
See picture below for an explanation.  Which should I choose to open he default applications?  I would like it to open the Ubuntu Software Center and install it.

---

### Post by gandaran on 2011-06-04
> **TAspr said:**
> See picture below for an explanation.  Which should I choose to open he default applications?  I would like it to open the Ubuntu Software Center and install it.
what exactly are you trying to do? ubuntu software center doesn't launch applications, USC installs applications from the repositories or .deb packages when you click them, it's already set as default to launch and install .deb packages, it doesn't install any other type of package.

---

### Post by TAspr on 2011-06-04
> **gandaran said:**
> what exactly are you trying to do? ubuntu software center doesn't launch applications, USC installs applications from the repositories or .deb packages when you click them, it's already set as default to launch and install .deb packages, it doesn't install any other type of package.

I was trying to run a file from the 

[http://www.getdeb.net/updates/ubuntu/10.10/?page=1](http://www.getdeb.net/updates/ubuntu/10.10/?page=1)

site, and when I click on the "Install This Now" button, this is what message comes up.

(See attached again)

---

### Post by TAspr on 2011-06-04
And for example, also, when I tell it to install the software, I get this error message: See pic.  come on now, I cannot keep doing this, someone's got to be able to explain why.

This has got to be the last time I am going to try and work this out, too frustrating for a newbie I tell you.

When I click on "OK" to install using the "Ubuntu Software Center" then I get the message above stating there is no "this or that" in your current software packages, and this does this for every program..

---

### Post by gandaran on 2011-06-04
> **TAspr said:**
> I was trying to run a file from the 

[http://www.getdeb.net/updates/ubuntu/10.10/?page=1](http://www.getdeb.net/updates/ubuntu/10.10/?page=1)

site, and when I click on the "Install This Now" button, this is what message comes up.

(See attached again)
did you follow the instructions adding getdeb to software sources (the repository and key)?
and you have to update the software package list after adding the repository either clicking the reload button on synaptic or running this command in terminal
```
sudo apt-get update
```
then you can find all getdeb packages in ubuntu software center.

---

### Post by TAspr on 2011-06-04
> **gandaran said:**
> did you follow the instructions adding getdeb to software sources (the repository and key)?
and you have to update the software package list after adding the repository either clicking the reload button on synaptic or running this command in terminal
```
sudo apt-get update
```then you can find all getdeb packages in ubuntu software center.


Ok, partner, I will try it.  At this point, I just want to throw this against the wall..

---

### Post by gandaran on 2011-06-04
> **TAspr said:**
> And for example, also, when I tell it to install the software, I get this error message: See pic.  come on now, I cannot keep doing this, someone's got to be able to explain why.

This has got to be the last time I am going to try and work this out, too frustrating for a newbie I tell you.

When I click on "OK" to install using the "Ubuntu Software Center" then I get the message above stating there is no "this or that" in your current software packages, and this does this for every program..
what software or package and from where?

---

### Post by TAspr on 2011-06-04
> **gandaran said:**
> did you follow the instructions adding getdeb to software sources (the repository and key)?
and you have to update the software package list after adding the repository either clicking the reload button on synaptic or running this command in terminal
```
sudo apt-get update
```then you can find all getdeb packages in ubuntu software center.

Please Provide pics of what I am supposed to do.  Old guy, with an odd eyeballs.

---

### Post by TAspr on 2011-06-04
> **gandaran said:**
> did you follow the instructions adding getdeb to software sources (the repository and key)?
and you have to update the software package list after adding the repository either clicking the reload button on synaptic or running this command in terminal
```
sudo apt-get update
```then you can find all getdeb packages in ubuntu software center.

So, by saying that running ***sudo apt-get update*** in the terminal, the applications will be available in the software center after downloading the Deb file??

---

### Post by gandaran on 2011-06-04
> **TAspr said:**
> So, by saying that running ***sudo apt-get update*** in the terminal, the applications will be available in the software center after downloading the Deb file??
if you have added the getdeb repository and key correctly for your ubuntu release then yes you can search and find every getdeb package in ubuntu software center or synaptic package manager

---

### Post by TAspr on 2011-06-04
> **gandaran said:**
> if you have added the getdeb repository and key correctly for your ubuntu release then yes you can search and find every getdeb package in ubuntu software center or synaptic package manager

Ok, now we are getting somewhere.  I appreciate your help and want to totally get away from Windows 7 as a dual boot, but some apps are just keep me coming back to Windows, as well as trying to figure out how to do everything in Ubuntu.. Drives you nuts I tell you.

thanks again for all your help.

---

