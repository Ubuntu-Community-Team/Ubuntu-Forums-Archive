---
title: "Bluetooth can't Receiving Files"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Its_Rishi on 2011-01-13
Default Bluetooth software given by ubuntu 10.10 does not receiving files from any other device
When i click on the bluetooth icon and selecting Preferences it opens a window of Bluetooth Preferences there is an option under it named "Receive Files" if i clicked it shows the following error

Error:
**"Cannot start "Personal File Sharing" Preferences**
Please verify that the "Personal File Sharing" program is correctly installed."

---

### Post by Its_Rishi on 2011-01-13
Can anybody Help me Please...
I am waiting

---

### Post by Elaztic on 2011-01-13
Hi,

Search for 'Personal File Sharing' in Ubuntu software center and install the program.

---

### Post by Its_Rishi on 2011-01-13
> **Elaztic said:**
> Hi,

Search for 'Personal File Sharing' in Ubuntu software center and install the program.
I Did but it shows the same Error...:(

---

### Post by Its_Rishi on 2011-01-13
Anyone help me please still iam waiting for the solution

---

### Post by keroman on 2011-01-22
click on bluetooth icon, a panel will open up, now you need to tick box"share publuc files over bluetooth"

also click recieve files in download folder over bluetooth

---

### Post by Mark_I_ on 2011-01-27
hello,
i had the same problem, after installing the package 'gnome-user-share' it works like a charm...
good luck..

---

### Post by ankit singh on 2011-01-27
Install Blueman bluetooth manager(its there in synaptic) and use that.

---

### Post by slick666 on 2011-02-08
> hello,
i had the same problem, after installing the package 'gnome-user-share' it works like a charm...
good luck..

Fixed my System

Thanks

---

### Post by anjexe on 2011-02-08
> **slick666 said:**
> Fixed my System

Thanks

worked for me too!:KS

mark as solved plz ;)
:lolflag:

---

### Post by Merlin2007 on 2011-04-06
In **Ubuntu 10.10** use **Ubuntu Software Centre**

**Applications>Ubuntu Software Centre**
In the **search box** type      ***gnome-user-share***
2 programs will show up, **Personal File Sharing** and **File Sharing**.

The one we need is **Personal File Sharing**.
**Click** on the **More Info **button. **Note:** It is a good idea to always click on the **More Info** button since,

You will see a description of the program, plus any **add-ons** you can add. **Put a check-mark on both add-ons**. **Click** the **Apply Changes** buttons.

Now, **Click** the **Install** button. Type in your password.
**Note:** Ubuntu Software Centre now tells you where the program is installed.
***Find it in the menu: System>Preferences>Personal File Sharing***.

**Close** **Ubuntu Software Centre**.

**Click** on the **Bluetooth Icon **(Notification area, Upper Right Corner of your Desktop) A menu will appear, **Click** on **Preferences**.
You will now see a window listing all paired devices. **Click** on the **Receive Files** button,
A new menu will appear,
Put a check-mark in **Receive files in Downloads folder over Bluetooth**,
**Accept Files:** You have an option for **Only for set up devices**, or **Always** by clicking the drop-down menu here. 
For a more secure environment I would recommend to only use the **Only for set up devices** option.
Putting a check mark on the **Notify about received files** is another good idea.

Now you should be able to enjoy the convenience of receiving files over Bluetooth.

You also have the **Share Files over Bluetooth** option. I have not played around with this option yet, I assume that you would need to put any files you want to share in a public folder??? If anyone knows the answer, please elaborate.

Sincerely,

Merlin2007

---

### Post by Exhack on 2011-05-02
Hi,
I recently upgraded to 11.04 (which is super BTW, thank you Canonical) but when I click on Bluetooth Preferences I get a prompt saying "Bluetooth is disabled". There's a button saying "Turn on Bluetooth", but when I click on it...nothing happens. Well it goes opaque but nothing else happens.

How does one enable Bluetooth?

PS Should have said that I performed the steps listed above and rebooted, but Bluetooth is still disabled.

Any advice would be welcome.

---

