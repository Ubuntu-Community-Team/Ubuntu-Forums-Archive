---
title: "Very Slow Internet - Need Help"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Spell-it-Out on 2009-05-04
Ok Just Start Of By Saying That I Have Almost No Idea What Im Doing Hence The Name Choice Because That Is What Im Needing Step By Step Really Simple Help.
I Have Possibly The Slowest Download Speed Ever. My Current Download Speed Is 4.4KB/s Dropping And Rising. I Am Using Ubuntu 8.10 Intrepid I Think Its Called? I Am A Uk Resident And Am With Virgin As My Internet Provider I Am Currently On Thier 10MB/s Plan Or Ment To Be :(. I Am Using Transmission To Download, I Have IPBlock/IPList Whatever It Is (A Friend Said It Could Be Useful) All My Torrents Have High Seeders And I Cant Seem To Get Fast Downloads No Matter What I Do. I Suspect Its The Connection Though Because My Internet Speed Isnt Very Fast Either (I Have Disabled IPV6, Using My Friends Advice Aswell) Didnt Really Notice A Huge Difference Though But Am More Concerned About My Downloads To Be Honest. I Dont Know What Information You Need To Know Before Helping Or How To Get It So If You Let Me Know I Can Give You Whatever You Need. Will Try _ANYTHING_ So Any Ideas Would Be Greatly Appreciated. 

Al :)

---

### Post by mprince on 2009-05-05
Make sure that under transmission Edit>Preferences that you haven't limited the download speed to 4K.

---

### Post by Spell-it-Out on 2009-05-05
Nah I Know I Said I Wasnt Very Good With Computers But I Know Atleast That :lolflag:
Both My Upload And Download Speed Are Unlimited. 

Al :)

---

### Post by mprince on 2009-05-05
Are you able to get better download speeds with firefox? Some ISPs do interfere with torrent downloads. Some even block seeding altogether.

---

### Post by Spell-it-Out on 2009-05-05
Not Sure What You Mean. If You Mean Just Downloading A File From The Net Then Yeah But Not Alot Better, Maybe 70KB/s Tops? I Havent Checked In A While. If It Would Help I Can Test It Out, If You Know A Way To Do It? When I First Upgraded To The Plan I Was Getting 160KB/s For Some Torrent Downloads Then It Just Completely Stopped. Im Not Sure If Its Something I Did Or Not Though.

Al :)

---

### Post by Spell-it-Out on 2009-05-05
P.s. Would IPBlock/IPList Not Stop The ISP From Blocking My Seeds?

Al :)

---

### Post by lavinog on 2009-05-05
There are various sites claiming that virgin throttles torrent traffic.
It is likely that there is nothing wrong with your setup.

Also make sure you are not allowing too many connections. There are many network devices that can not handle more than 50 concurrent connections.
It is very common to see users configure their torrent client to use 200+ connections, thinking more connections mean greater bandwidth.  Some routers can crash with too many connections.
torrents are not meant to be fast, just reduce bandwidth from hosting sites. They are most effective when ran over a long period of time (allows for more seeders.)
Also torrent dl rates can be regulated by you seeding ratio...if you are not seeding, then you will have a lower priority on the queue.

---

### Post by Spell-it-Out on 2009-05-05
So Theres No Way Around It Except From Changing My Provider? :(

Nah I Have A Max Of 200 Connections And 150 Per Torrent, I Tried It Because There Is Almost No Way Of Me Having More Than That Anyway.

Yeah Im Not Expecting Them To Be Crazy Fast Just Not Crazy Slow, Its Just That I Used To Be Able To Get 100KB/s Plus And Now I Cant Seem To Get Over 7KB/s If That.

I Always Seed Because I Never Bother To Turn Off The Computer, (Most Of The Time Because I Download Over-Night). What I Used To Do Was Limit My Upload Speed Completely Then After The Files Were Downloaded I Used To Turn The Upload Speed Back Up. But Even Then I Didnt Really Get A Huge Result My Upload Speed Was Significantly Higher When I Did It That Way Though, As If It Was All Building Up. :confused:

Im Still Stumped So If You Have Any Other Ideas On What I Can Do, Or Check Or Whatever Then Please Let Me Know.

Al :)

---

### Post by lavinog on 2009-05-05
> **Spell-it-Out said:**
> 
Nah I Have A Max Of 200 Connections And 150 Per Torrent, I Tried It Because There Is Almost No Way Of Me Having More Than That Anyway.

My point was that 200 connections is pretty high for alot of networks. There is additional overhead for each connection.
See if you see a difference with just 50 connections.

---

### Post by Spell-it-Out on 2009-05-05
Ok Im Giving It A Go Although I Worked Out What Was Wrong And You Wouldnt Believe It. :shock:

I Have Been Doing Speed Tests For The Past Couple Of Days And Trying To Find Trends Or Areas Of Improvement Etc.
So After All This Time Searching Through Forums, FAQs And Help Guides, I Decided To Phone My ISP (Virgin Media) And Spoke To Them About The Problem. It Turns Out That Even Though They Have Been Charging Me For Ages For 10MB/s My Maximum Has Been In The 0.3MB/s Region, The Reason For This Is That My Cable Modem Is Now Obsolete And Can Not Pick Up That Kind Of Speed. So After A While Of Arguing They Are Sending Me A New Modem For Free (Which In My Opinion They Should Have Done From The Begining) But What Can You Do. Thanks Alot For All The Advice.

Al :)

---

