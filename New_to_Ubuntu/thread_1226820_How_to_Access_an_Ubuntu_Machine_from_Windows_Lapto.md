---
title: "How to Access an Ubuntu Machine from Windows Laptop in a WIired Network"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by anzaksonn on 2009-07-30
[SIZE=2]Hello good friends!!!  I am a Newbie in the world of UBUNTU, so please bear with me! I have a laptop with WindowsXP Professional sp3  & [/SIZE][SIZE=2]a desktop with Ubuntu 9.04. I've connected the two through a wired network that works just fine from the Ubuntu machine.The icon for the Windows Laptop appears and I can access the whole machine and all its contents. But the other way around is not working. In Windows' "My Network Places," I can _only_ see and access individual folders that have been marked "share" in the Ubuntu machine. The icon for the Ubuntu machine doesn't appear. Neither does it appear in "Show Computers in Workgroup!" In Samba config, I have changed the Workgroups name to the current one, and saved it. I've re-checked and seen that the Workgroups name _is_ the current one. I've also changed Security = **share**  and force user = **nobody** and force group = **nogroup **and saved them.
            I'm self-learned when it comes to computers so I'm very bad at technical terms.
Please, can anyone give me a solution in steps and language that I can comprehend.

The forums here are just _EXCELLENT. _I thank, from the bottom of my heart, all of you who are making the effort to share your knowledge with us newbies!!! Take care and please keep up the excellent work. [/SIZE][B]:):):)



SPECIFICATIONS:

LAPTOP: DELL LATITUDE D 400;       OS: Windows XP Professional SP3;                                               CPU: Intel Pentium M 1.60GHz
RAM:  512 MB;                                                    HDD:  27.9 GB;  10 GB free;  
GRAPHICS CONTROLLER:  Intel 82852/82855/GM/GME

DESKTOP: OS: UBUNTU 9.04               CPU:   AMD ATHLON 64, 4000+
MOTHERBOARD: ASUS A8N-E                   GPU:  G72 GE FORCE 7300 LE
RAM:  1024 MB;                                      HDD: 160 GB,  120GB free   
[/B]

---

### Post by QIII on 2009-07-30
I think you are seeing the behavior you want to see.

You've told Ubuntu what you want anyone else to see (the shared folders), and that is all it is going to let anyone else to see.

Windows can be sloppy.  All of my Ubuntu machines can see the entire drive on my Windows machines.  From my Ubuntu machines, I could conceivably delete a critical system file from my Windows machines out of spite.  My Windows machines can only see my shares in Ubuntu.

Why do you need Windows to see everything on your Ubuntu machine?  Just put what you want to be public in a share.  Why on earth would you want to expose things like your system files on your Ubuntu machine to Windows?

---

### Post by anzaksonn on 2009-07-30
[SIZE=2]Thank you  **QIII**, for your input. You do have a valid point in what you say. However, the laptop with Windows installed is my son's. He has permission to access whatever folders and files that I have. So it's a matter of convenience, really. I can, of course, sit down and make all the folders in my Ubuntu machine share permitted individually, if that's what is needed. But right now I don't have the time. I don't know in advance what folder or file he would want to access or when. So it would be convenient if he could access the whole machine and search and find for himself, just as I can access his and find whatever I need for myself. 

Thank you again, QIII!!! I hope there's a solution to my little problem.[/SIZE]

---

### Post by QIII on 2009-07-30
What folder or file would he need to access except for those which you previously give him permissions?  Do you need him to look at /etc?

At work, does your LAN administrator give you unlimited access to all the files on each of the computers on the LAN?  Likely not.  He most likely has a shared folder on some machines that can be mapped as a network drive for common use.

My recommendation, for what it's worth, is to do exactly what you said you didn't want to do:  determine from the beginning what you want to give him access to an keep that in a share.

When my kids were younger, they didn't have access to the liquor cabinet or the gun safe.  They did have access to the fridge and the pantry.

---

### Post by anzaksonn on 2009-08-01
**Thank you **very much, **QIII**, for your inputs. I appreciate it very much!!! My son is a wonderful young man and there's nothing in my computer (or even in my life for that matter) that he's not allowed access to. 
    Seems like I'll have to share-permit folders manually as and when he needs them. Since no one else has come forward with any solution, I surmise that there isn't one. I'll continue to learn more about Ubuntu when I find the time. There are literally tons of stuff that I must learn.
   Take care, QIII!!!:)

---

### Post by HiImTye on 2009-08-01
**I strongly recommend that you do not share your entire filesystem**, exposing it on the network (and conceivably an *external* network). that being said,

if you want to give him access to the entire filesystem then open up *nautilus* (File Browser). on the left pane, click the drop down and select '*tree*'. now right click on '*File System*' and go to *Share*. 

what I would recommend is to instead, share '*/home*' and '*/media*' - this will give access to basically everything that will *need* to be shared.

---

### Post by anzaksonn on 2009-08-04
[B][SIZE=2]Hello Tye!!!
                      Thank you so much for your suggestions. [/SIZE][/B][SIZE=2]I agree totally with you about sharing everything in a wider network. Its not my intention either. It's for my son and only my son that I want to share-permit the whole filesystem!  Your suggestion seems to be perfect and I'll try that out and if that seems to be enough, then I'll stick to it. I'm really enjoying working with Ubuntu 9.04 and constantly learning new things!!!  :)
                Thank you once again for sharing your knowledge. I hope I can learn more from you as and when I encounter any other problems. Take care and have a great week!!!   :) 
[/SIZE]

---

### Post by HiImTye on 2009-08-04
you're welcome, hope everything works out for you :)

---

