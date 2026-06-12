---
title: "Cannot acess SMB when WD Mybook Goes to sleep"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by Dustout on 2008-02-25
I am currently sharing files over SMB using my external 500GB WD Mybook, it works great until the hard drive decides to go into sleep mode (happens after about 20min of inactivity). When it goes to sleep i am unable to access files via SMB and i have to manually access a random file on the hard drive to get it out of sleep mode.

I was hopeing their was a way to either disable sleep mode or change the SMB share to fix this.


edit - a possible solution may be a simple program that accesses the hard drive every x min, or better yet a program that does that when a SMB share is acesses...dont know how hard that would be but if its dooable i'd probably be able to make it

---

### Post by OpenFish on 2008-02-25
are u after some thing like this with
[http://www.karakas-online.de/gnu-linux-tools-summary/scheduling.html](http://www.karakas-online.de/gnu-linux-tools-summary/scheduling.html)
with a simple 'cp file1, file2' i havent used this but i think its what u want 

the best solution would be to turn off sleep or evan better get it to wake up but i dont have one to play with so wait for another post, have a good google or have a go with the above 

good luck!!

---

### Post by Dustout on 2008-02-25
I can see how adding a cron job would fix the problem, but i was hopeing for a more elegent solution.

getting it to 'wake up' automatically worked when i shared files in windows, but in linux it doesn't seem to have the same effect :(

i gave google another try, and the only thing i could find was a mention of an issue of SMB issues with mac's (2nd last post here [http://forums.macrumors.com/archive/index.php/t-300586.html](http://forums.macrumors.com/archive/index.php/t-300586.html))

---

### Post by benfindlay on 2008-05-02
Not sure if you solved this, but I went down the route of a cron job using the following command```
*/5   *   *   *   *   touch '/path/to/drive/.temp'
```
Hope this helps!

---

