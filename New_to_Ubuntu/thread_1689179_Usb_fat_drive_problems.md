---
title: "Usb fat drive problems"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by CCompton on 2011-02-16
I know this is probably a repeat question, because I have bee scouring this site to figure out my problem. But please bear with me , and maybe point me where to go.
    OK, About 3 months ago I purchased and 500gig external drive to expand my FTP servers storage space. From the start, plugged it into a MAC  and formatted it FAT so I could possibly read it on multiple computers....I then plugged it into the Kubuntu box that Im running GPRO FTP on, and BAM! It worked, worked GREAT. Auto-mounted it right from the start I could read and write to it , I immediately began putting files on it and shared it out to my network. I could see it from all the other machines in my network (99% Mac Network) NO PROBLEMS. I could read and write to it and All was right with the world.
   YESTERDAY, out of the blue, no changes , I CHANGED NOTHING PEOPLE, it suddenly became read only. Maybe the linux machine restarted on its own over night for some strange reasone, maybe I got hacked. Dont know.[COLOR=DarkRed] But now the drive is read only, and to add insult to injury , the drive wont mount on any of the other machines in the network,  ( I can see the drive but it wont mount). [/COLOR]

---

### Post by sydbat on 2011-02-16
> **CCompton said:**
> I know this is probably a repeat question, because I have bee scouring this site to figure out my problem. But please bear with me , and maybe point me where to go.
    OK, About 3 months ago I purchased and 500gig external drive to expand my FTP servers storage space. From the start, plugged it into a MAC  and formatted it FAT so I could possibly read it on multiple computers....I then plugged it into the Kubuntu box that Im running GPRO FTP on, and BAM! It worked, worked GREAT. Auto-mounted it right from the start I could read and write to it , I immediately began putting files on it and shared it out to my network. I could see it from all the other machines in my network (99% Mac Network) NO PROBLEMS. I could read and write to it and All was right with the world.
   YESTERDAY, out of the blue, no changes , I CHANGED NOTHING PEOPLE, it suddenly became read only. Maybe the linux machine restarted on its own over night for some strange reasone, maybe I got hacked. Dont know.[COLOR=DarkRed] But now the drive is read only, and to add insult to injury , the drive wont mount on any of the other machines in the network,  ( I can see the drive but it wont mount). [/COLOR]I really do not have an answer for you at the moment. Perhaps it is physically failing?

Also, I am not sure why you chose FAT. You could have just formatted HFS Plus or ext2/3/4...especially since your network is almost all Mac/Linux.

---

### Post by CCompton on 2011-02-16
Well, there are PC's on the network as well,...and I thought I would leave my options open,..and really IM not sure why I did it....(note , we are in the absolute beginers forum ;)  )

The drive is fine,  as far as I can tell, I can read from it and from terminal logged in as root , I can read and write to it fine. The problem is I need to access it from the network to make it useful. Its an FTP storage / holding place .

Im wondering if I shouldnt copy the files off and re format it.....which would you suggest?

---

### Post by sydbat on 2011-02-16
> **CCompton said:**
> Well, there are PC's on the network as well,...and I thought I would leave my options open,..and really IM not sure why I did it....(note , we are in the absolute beginers forum ;)  )

The drive is fine,  as far as I can tell, I can read from it and from terminal logged in as root , I can read and write to it fine. The problem is I need to access it from the network to make it useful. Its an FTP storage / holding place .

Im wondering if I shouldnt copy the files off and re format it.....which would you suggest?If you can fully access it with root permissions, it somehow has had it's permissions changed.

I would definitely back up first, before doing anything else.

Then, try [this solution]("http://ubuntuforums.org/showpost.php?p=1266095&postcount=3") (from a few years ago, but it ***should*** still work).

If that does not work, reformatting may be the solution.

---

