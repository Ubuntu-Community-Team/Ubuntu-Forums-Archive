---
title: "How to share my laptop with Desktop computer"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by DayLite on 2010-08-02
My desktop is a wired connection and my laptop is connected via my wireless router, both are using Ubuntu 10.04.

How do I allow my laptop to see my external Drive that is connected to my desktop, also to connect with my printer.

---

### Post by AlphaLexman on 2010-08-02
Here is a good tutorial: [http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

---

### Post by binselam on 2010-08-02
Hi,

You might like to consider installing SAMBA onto you desktop. You can access your desktop resources using SAMBA share.

Here is a link that shows SAMBA installation.

[http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/)

Good luck

---

### Post by DayLite on 2010-08-02
Thank you both for you kind replies :)

I will now try to take your suggestions and see if I can make it work.

---

### Post by DayLite on 2010-08-02
> **AlphaLexman said:**
> Here is a good tutorial: [http://principialabs.com/beginning-ssh-on-ubuntu/](http://principialabs.com/beginning-ssh-on-ubuntu/)

I read the article:
> The following assumptions are made about the reader:
  
[LIST]
[*]You know what a terminal/command line/shell is and how to start a session.
[*]You have at least a basic familiarity with Linux/Mac command-line syntax.
[*]You’re on a private LAN with access to at least two Linux/Mac  computers (or, you have a user account on a remote server that accepts  SSH connections).
[/LIST]


I am new and do not understand :(

---

### Post by JustinR on 2010-08-02
Hi, the easiest way to do this is to install Samba, ***on the computer with the printer and external hard drive.***

In Ubuntu the packages are:

[B]samba
system-config-samba[/B]

So go into **Applications > Accessories > Terminal**

In the terminal type:
```

sudo apt-get install samba system-config-samba

```
Enter in your password and it will install Samba for you. Alternatively, you can go to System > Administration > Synaptic Package Manager if the terminal makes you uncomfortable.

The package 'system-config-samba' is a GUI for the package 'samba'.

--

Go to **System > Administration > Samba**.

Click the big + sign button. Since you said you wanted to share your external hard drive, click the big browse button and find where your hard drive is (eg. /media/EXTERNALHARDDRIVE). Type in a short share name such as 'ExternalHDD' or something along those lines. You can leave 'Description' blank and click both check boxes at the bottom called 'Writable' and 'Visible'. Under access click 'Allow access to everyone', or if you want to be more secure just click the checkbox that's next to your username. Press 'Ok'.

To share your printer, go to **System > Administration > Printing**. Find your printer, right click it, and press 'Shared'. Done!

-- _* Do the rest of this on the computer **with out** the printer and external hard drive. *_

On the other computer (the one without the printer and External hard drive), to go **Places > Network**. The computer with the printer and external hard drive should pop-up. Double click it, if it asks for a password just enter in the Username and Password of the computer with the printer and hard drive in. Now, you should see your hard drive! You can create a link to it to your desktop if you want.

To get access to the printer go to **System > Administration > Printing**. Click the button called 'Add'. A dialogue should pop up, click 'Network Printer' and click 'Find Network Printer'. It will search for printers, if your's is found then press 'Forward' and continue until the dialogue is closed. If it is not, then click 'Windows Printer via SAMBA', click the 'Browse' button and find the computer with the printer on it, click the printer name and press 'Forward'. Then your finished!

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Hi, the easiest way to do this is to install Samba, ***on the computer with the printer and external hard drive.***


I read articles on Samba, it said that it wasn't secured and possible to be hacked into. Both of my PC's are in my living room. I want to make sure the communication remains here in my living room, not on the world wide web.

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> I read articles on Samba, it said that it wasn't secured and possible to be hacked into. Both of my PC's are in my living room. I want to make sure the communication remains here in my living room, not on the world wide web.

Pretty much everything is hackable, SAMBA is no different but it shouldn't be a cause of alarm for you. If your using a password protected router then you should be fine.

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Pretty much everything is hackable, SAMBA is no different but it shouldn't be a cause of alarm for you. If your using a password protected router then you should be fine.

My router is password protected. But what is odd is that when my laptop saw my wireless, I used the key to connect, not the password.

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> My router is password protected. But what is odd is that when my laptop saw my wireless, I used the key to connect, not the password.

Thats how routers work - you use a Username and Password to login to the administration interface of the router and to get internet access from the router you use a key code - if your using a key code on your routher then most likely, SAMBA will never be hacked into. A hacker would actually have to be on your network - which means that they would also have to have your network key code, which, unless your giving your key code out should never happen.

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Thats how routers work - you use a Username and Password to login to the administration interface of the router and to get internet access from the router you use a key code - if your using a key code on your routher then most likely, SAMBA will never be hacked into.

Thanks:D

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> Thanks:D

Your welcome! Have fun.;)

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Thats how routers work - you use a Username and Password to login to the administration interface of the router and to get internet access from the router you use a key code - if your using a key code on your routher then most likely, SAMBA will never be hacked into.

Thanks:D  I will post "success" when I get it to work. I want to than you very much for helping me and responding so quickly.  I really appreciate you, very much ):P

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> .

I installed it and I can see my external drive on my laptop. 

:confused: Doesn't open It says

>  **Unable to mount location** Failed to mount windows share  

Please help :(

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> I installed it and I can see my external drive on my laptop. 

:confused: Doesn't open It says



Please help :(

Try restarting both computers and try again.

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Try restarting both computers and try again.

I rebooted both computers, still the same problem , won't mount.:(

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> I rebooted both computers, still the same problem , won't mount.:(

Okay, try this command:
```

sudo mkdir /media/ExternalHDD
sudo mount //COMPUTERNAME/EXERNALLHDD /media/ExternalHDD

```

Replace 'COMPUTERNAME' with what showed up in 'Network'.

And EXTERNALHDD with the Share name of the external hdd you put in SAMBA.

If you have a password on the Share then the command is:
```

sudo mount //COMPUTERNAME/EXTERNALHDD /media/ExternalHDD/ -o user=username,pass=password

```

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Okay, try this command:
```

sudo mkdir /media/ExternalHDD
sudo mount //COMPUTERNAME/EXERNALLHDD /media/ExternalHDD

```Replace 'COMPUTERNAME' with what showed up in 'Network'.

And EXTERNALHDD with the Share name of the external hdd you put in SAMBA.
[/code]

Didn't work :(

>  sudo: mk: command not found
:

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> Didn't work :(

The command is 'mkdir' not 'mk' ;)

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> The command is 'mkdir' not 'mk' ;)

typed it wrong, I did put in terminal mkdir

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> typed it wrong, I did put in terminal mkdir

Okay well instead of doing 'mkdir' just do the 'sudo mount' command in my previous post and mount it to '/mnt' instead of '/media/EXTERNALHDD'

So basically:
```

sudo mount //COMPUTERNAME/EXERNALHDD /mnt

```

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Okay well instead of doing 'mkdir' just do the 'sudo mount' command in my previous post and mount it to '/mnt' instead of '/media/EXTERNALHDD'

So basically:
```

sudo mount //COMPUTERNAME/EXERNALHDD /mnt

```

Followed your instructions :(

What is very :confused: I was able to set up the printer on my laptop to recognize and print to my desktop printer, yet cannot mount the external hard drive or my photo folder on my desktop.

---

### Post by JustinR on 2010-08-02
> **DayLite said:**
> Followed your instructions :(

What is very :confused: I was able to set up the printer on my laptop to recognize and print to my desktop printer, yet cannot mount the external hard drive or my photo folder on my desktop.

Well I'm not sure what else I can do for you - you can try searching Google for 'Unable to mount location Failed to mount windows share'

---

### Post by DayLite on 2010-08-02
> **JustinR said:**
> Well I'm not sure what else I can do for you - you can try searching Google for 'Unable to mount location Failed to mount windows share'

Thank you for your effort and taking your valuable time to help me. I have been doing a Google search to no avail.  Many of the posts have no solutions, just questions.

Thanks again, and take care.

---

