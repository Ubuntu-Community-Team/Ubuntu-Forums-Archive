---
title: "how do I find the gz file that Evolution created as a backup??"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-02-20
Hi Ubuntu Community:

A few weeks ago I deleted all of the files on both my home and backup hard disks.

Fortunately, I turned my computer off immediately and started the process of recovering my lost files. I'm writting a "how to" on the forums so that people who get into the same situation can find resources on how to recover files. See: [http://ubuntuforums.org/showthread.php?t=1675564]("http://ubuntuforums.org/showthread.php?t=1675564")

I used **[COLOR="Red"]photorec[/COLOR]** to recover my files.

Among the file types that I asked [COLOR="Red"]**photorec**[/COLOR] to recover were all of my gz files. I use Evolution and create a weekly backup of my entire [COLOR="Blue"]**Evolution**[/COLOR] data.

However, [COLOR="Red"]**photorec**[/COLOR] recovered thousands of gz files and it isn't obvious to me which one is my [COLOR="Blue"]**Evolution**[/COLOR] gz backup file.

Can someone advise me on how I'd comb thru all of my recovered gz files to determine which one is my [COLOR="Blue"]**Evolution**[/COLOR] backup gz archive?

Thank you!
Phil Smith
Duluth, GA

---

### Post by Keiran230 on 2011-02-21
I'd try creating another backup, then looking at the filename. It might have a pattern. Then, I'd search for that name. You can use * as a wildcard when searching files.

one way to find it once you know the name: updatedb && locate file.tar.gz

---

### Post by Keiran230 on 2011-02-21
I looked it up, and I believe the default naming is evolution-backup.tar.gz

---

### Post by Old Jimma on 2011-02-24
Hi Kieran:

Thanks for your work. 

About a month ago I wiped out my home HD and backup HD. I had saved the evolution backup file.

I used photorec to recover all of my files, including all gz files.

I did a find on the gz files to find a string that I knew was in my evolution file, like "Brocton" because I know it is a name of a town the I saved in my Evolution contacts.

The find did find the gz file. HOwever, evolution was not happy with the gz file for some reason.

Phil

---

