---
title: "Trouble configuring my home network"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by techiewannabe on 2009-08-20
Okay...I'm sorry, but I'm really lost on this..

I am trying to configure Ubuntu's latest version so that it will work with my home network. My home network is comprised of three other computers, all using Windows programs. I can't figure out how to "see" the rest of my network. I have been able able to access the Internet in my network, but I can't seem to do anything else. I can't "see" the other computers. I can't "see" the printer.

I know that there are documents out there that deal with configuring my system but I can't seem to make this work. For example, a document tells me that I can mount my network connection if I right click an icon, and choose "mount." Unfortunately, "mount" is not an option that I see. 

Do any of you have a document that can walk me through this? I would appreciate it.

Thanks.

Techiewannabe.

---

### Post by lisati on 2009-08-20
Click on Places->Network
This should open up a window showing the networks and other computers that your computer can "see".

---

### Post by mapes12 on 2009-08-20
Hi

On the other machines you will need to enable file a print sharing and also enable sharing for the specific folders you want to share across the network.

In order to see them from your ubu box install pyNeighborhood. It's in Synaptic. When installed go to Edit>Preferences then change the mount point from /mnt/lan to /home/*username*. This will mean you don't need root permission to access the other machines. Also, tick the box "remove mount points after unmount".

Left hand pane right click "Groups" then "Scan". It should then show your other machines where you can double click away into the shared resources.

That's how I got mine working yesterday.

Mark

---

### Post by techiewannabe on 2009-08-20
Thanks to Lisati and Mapes12:

I did exactly what each of you suggested. However, I am still only able to "see" my Linux computer. I can't "see" any other computer in my network. (I should be able to see two others.)

If you have other ideas, I'd love to hear them. 

I suspect that there is a simple answer, but I am a newbie and haven't yet wrapped my mind around the logic of the Linux systems.

Thanks.

Techiewannabe.

---

### Post by mapes12 on 2009-08-21
I found a good tutorial on Youtube showing how to share your stuff on Ubu with other machines on your LAN: [http://www.youtube.com/watch?v=89hjWOb8qmY&annotation_id=annotation_888326&feature=iv](http://www.youtube.com/watch?v=89hjWOb8qmY&annotation_id=annotation_888326&feature=iv)

Enabling windoze to share is as I posted last time but beware if you have more than one user account on the windoze machine. If the account has limited permissions on windoze you have to assign it admin permssions otherwise the share won't work. It took me 3 days to work this out.

Mark

---

### Post by jonandrews on 2009-08-21
I have put some step-by-step illustrated guides on networking in a mixed Ubuntu / Windows network on my website:
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by techiewannabe on 2009-08-23
Thanks everyone for help. I was able to configure my system so that I can "see" the other computers. 

Now I have a related problem .......:) I'm not sure if I should post it as a new thread or not.....

When I view my network the other computers get "mounted." Then I can't unmount them! In fact, the only way that I have found to unmount them is to reboot the system.

Your help, please...

Tom

---

### Post by mapes12 on 2009-08-23
If you're using PyNeighbourhood you right click the share you want to unmount there should be a sub menu pop up with unmount as an option. Also, tick the box "remove mount points after unmount" in Edit>preferences .

---

### Post by techiewannabe on 2009-08-23
Thanks very much! It worked like a charm. :)

Now about configuring my printer on the network.... Can you steer me towards a good tutorial.

You've been very helpful.

Tom

---

### Post by Iowan on 2009-08-23
[https://help.ubuntu.com/community/Printers]("https://help.ubuntu.com/community/Printers")
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

---

### Post by techiewannabe on 2009-08-25
Iowan: 
  	 	 	 	 	 	  

Thanks for your posting.  
 

 I've tried to follow the directions that are offered at the webistes, but still have trouble configuring the printer. My Linux system doesn't “see” my network printer. Here are the steps that I am following in my efforts to configure the printer.  
 

 System > Administration > Printer.  
 Then I go to Server > New > Search.  
 It searches for a printer.  
 I choose 'Network Printer.'  
 I choose 'Windows Printer via Samba.'
 The screen prompts me for data on 'SMB Printer.'
 I have tried every piece of information that I can think of to follow the prompt of : [smb://]("smb:///"). After putting the data in, I click “Browse.”  
 I have never been successful in finding the printer which is located on my network.  
 

 I'm guessing that I am not putting in the correct “language” to identify the printer. Apparently, I don't understand the language, yet. 



 I have not yet wrapped my mind around the logic of Linux systems. I know that, eventually I'll get it, but I'm not there yet. 

 I would love to hear some ideas about solving this problem.  
 

 Thanks again for your help.
 

 Tom

---

### Post by techiewannabe on 2009-08-25
Whoops! I accidentally sent a message twice. I deleted the message but now I don't know how to delete this text box! 
Tom

---

