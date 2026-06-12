---
title: "more Ubuntu and windows networking"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by VoyeurOne on 2007-10-02
Good evening everyone.

I am having problems seeing my wireless windows XP sp2 laptop from my Ubuntu desktop.
I can get and send files to Ubuntu from my laptop, I can even print to my Ubuntu printer from windows but unfortunately it's a one way street, I cannot see my windows network, my laptop or my laptop shares from Ubuntu.  

Obviously both computers are communicating at some level otherwise I would not have a flawless one way from the windows laptop to my Ubuntu desktop.

smbtree shows all of my network including laptop and shares on laptop,  unfortunately that terminal listing is the only place from which I can tell the laptop exists on the network from my Ubuntu machine.

I know I'm close but I need some help to get past this point.

Thanks

---

### Post by VoyeurOne on 2007-10-03
Anyone????  

I would think that I am close enough that it's a simple configuration I'm missing

---

### Post by helgman on 2007-10-03
This is a long shot but ...

... maybe your wireless AP is using some kind of wireless isolation, not allow communication to computers connected via the wireless interface? I've never played around with it myself.

I've had a problem just like yours while helping a neighbor of a relative. I never had time to get to the bottom of it but the scenario was pretty much the same as the one you describe. We could make a one way connection. Since we where only going to move a big chunk of files (a one time job) we connected the laptop to the router via a cable and got the work done.

Does this help at all?

Regards,
Helgman

---

### Post by helgman on 2007-10-03
Here a two other things that I should have thought of:

*) Have you ever been able to use the shared folders on the Windows machine?

*) Can you connect to the machine using smb://*IP address of Windows machine*?

Regards,
Helgman

---

### Post by VoyeurOne on 2007-10-03
Hi thanks and thanks for the reply.  If I boot both machines to windows the chat away trading files and germs but once I load Ubuntu on the desktop the only one doing the chatting and the transfrering is the laptop with windows.   The listing in Terminal gives me the full network with all the shares but I can't see the network in places or in network setup.  I am sure th eproblem is a missing file or link in the Ubuntu machine but which one

---

### Post by helgman on 2007-10-03
I'm not sure I'm with you all the way here. Have you tried opening a file browser and connecting to the Windows Machine per the instruction above?

I've noticed that if the WORKGROUP is set different on the Ubuntu box then on the my Windows box(es) then I can't find them on the network, so make sure that they are the same. I'm having a bit of a problem reproducing the problem here I'm afraid so that was the best I could do just now ...

Regards,
Helgman

---

### Post by VoyeurOne on 2007-10-03
I know it's strange my laptop transfers files to and from my Ubuntu and prints to the Ubuntu printer.

My smbtree listing shows the entire network

MSHOME
        \\UBUNTU                        Ubuntu server (Samba, Ubuntu)
                \\UBUNTU\IPC$                   IPC Service (Ubuntu server (Samba, Ubuntu))
                \\UBUNTU\pierre Ubuntu  
                \\UBUNTU\IAUDIO         
                \\UBUNTU\TRANSFERS      
                \\UBUNTU\FreeAgent Drive
                \\UBUNTU\deskadult      
                \\UBUNTU\LinuxAdult     
                \\UBUNTU\LinuxMovies    
                \\UBUNTU\LinuxMusic     
                \\UBUNTU\deskpictures   
                \\UBUNTU\deskmusic      
                \\UBUNTU\deskmovies     
                \\UBUNTU\linuxpicture   
                \\UBUNTU\print$                 Printer Drivers
        \\LAPTOP                        Laptop
                \\LAPTOP\D laptop       
                \\LAPTOP\C Laptop       
                \\LAPTOP\shares         
                \\LAPTOP\Fiftieth       
                \\LAPTOP\My Music Laptop
                \\LAPTOP\My Videos      
                \\LAPTOP\SharedDocs     
                \\LAPTOP\print$                 Printer Drivers
                \\LAPTOP\IPC$                   Remote IPC
                \\LAPTOP\Pictures on Laptop

My problem is that I can't figure out how to see the laptop from Ubuntu, it's not in the places menu,  If I go to Connect to Places/connect to network  my MSHOME doesn't show up as an option.  I know both computers are connected but for some reason I can't get to the laptop from Ubuntu??

---

### Post by VoyeurOne on 2007-10-03
Opps forgot one thing

pierre@Ubuntu:~$ smb://192.168.0.102
bash: smb://192.168.0.102: No such file or directory
pierre@Ubuntu:~$ 

That doesn't work either

---

### Post by Lambert on 2007-10-03
Have you read this guide?

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

---

### Post by helgman on 2007-10-03
> **VoyeurOne said:**
> pierre@Ubuntu:~$ smb://192.168.0.102
bash: smb://192.168.0.102: No such file or directory
pierre@Ubuntu:~$ 

That doesn't work either

No, I didn't know your did it via the command line, the first post says Ubuntu desktop, so I figured you'd fire up the file browser and go to work on the address bar. The link above should do the trick since there are information about mounting shares via the CLI.

Good luck!

Regards,
Helgman

---

### Post by VoyeurOne on 2007-10-03
Oh WOW, I'm scared to do all that again, I have a flawless connection going one way I think I will just contunue to do all my transfers from the laptop rather than risk loosing what already works...

Thanks folks

---

### Post by VoyeurOne on 2007-12-08
I suppose we could call this one closed, I re-installed Feisty and everything worked out of the gate so I still don't know what I had messed up in the first install but the re-install solved my problem.

---

### Post by Lostincyberspace on 2007-12-09
It sound like you didn't have samba installed right or something.

---

