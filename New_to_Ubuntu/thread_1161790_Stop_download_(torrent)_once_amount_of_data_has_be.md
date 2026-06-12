---
title: "Stop download (torrent) once amount of data has been reached"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by laffinet on 2009-05-17
Hi !

I've got a data allowance with my ISP and was wondering if it is possible to automatically stop a torrent (or multiple torrents) once a certain amount of data has been downloaded (or uploaded). I am trying to prevent going over my allowance and get shaped as a consequence without having to check manually.

Cutting the whole network connection (or shutting down the computer) once a certain amount of data has been reached would be fine too. So maybe a script that monitors the data traffic and triggers an event once traffic reached a limit would do it ?

Thanks for any help.

---

### Post by diablo75 on 2009-05-17
I think you can do something like this with a torrent client like Deluge but it's been a while since I've used it.  I think at the very least you can tell it to stop downloading once a file is complete, or even once you've reached a certain share ratio.

---

### Post by kpkeerthi on 2009-05-17
Yes. Deluge can do this. 

Under its Preference -> Queue, you can set:

1. How many torrents you want active a time.
2. How many torrents you want seeding at a time. 
3. You can also specify how long you want the seeding to continue, based on share ratio.

The options are well laid out and intuitive. 

To install deluge, select Applications -> Add/Remove. Search for **deluge** and install it.

---

### Post by laffinet on 2009-05-17
Thanks for the replies.

Unfortunately unless I'm missing something I don't this is exactly what I'm trying to do. 

I don't want to set a seeding limit, I want to stop downloading once a certain amount of data (say 2G) have beend downloaded. Not sure how I could achieve this with the seeding limit.

---

### Post by Keithhed on 2009-05-17
I am familiar with Deluge and am not aware of a "download" limit.  You may just have to exercise caution with how many items you choose to get

---

### Post by binbash on 2009-05-17
[https://forum.deluge-torrent.org/viewtopic.php?f=9&t=9665](https://forum.deluge-torrent.org/viewtopic.php?f=9&t=9665)

---

### Post by kpkeerthi on 2009-05-17
-- deleted --

---

### Post by mister_p_1998 on 2009-05-17
> **laffinet said:**
> Thanks for the replies.

Unfortunately unless I'm missing something I don't this is exactly what I'm trying to do. 

I don't want to set a seeding limit, I want to stop downloading once a certain amount of data (say 2G) have beend downloaded. Not sure how I could achieve this with the seeding limit.

My ISP allows me to download 30GB per month between 18:00 - 0:00am weekdays, outside of those times its not measured, so I do my torrents between 12:00 am and 6:00pm. You need to schedule your Torrent program (I use ktorrent which has a scheduling plugin) to ONLY download in your UNMEASURED period of connection. Do you have an unmeasured period? Check with your ISP. If your connection is measured all the time, you may have a problem. Its worth installing a program called vnstat, its shows your data up/downloads totals by month, day or week. Heres an example of my laptops data log:

steve@Gutsy-Vaio:~$ vnstat -m

        eth1

           month        rx      |       tx      |    total
        ------------------------+---------------+---------------
          Jun '08     29259 MB  |      3278 MB  |     32538 MB
          Jul '08     43728 MB  |     11254 MB  |     54983 MB
          Aug '08     38019 MB  |      7414 MB  |     45433 MB
          Sep '08     35357 MB  |      3590 MB  |     38948 MB
          Oct '08     46219 MB  |      3320 MB  |     49540 MB
          Nov '08     61300 MB  |      8615 MB  |     69915 MB
          Dec '08     33673 MB  |      1823 MB  |     35497 MB
          Jan '09     55414 MB  |      8006 MB  |     63421 MB
          Feb '09     32380 MB  |      3461 MB  |     35841 MB
          Mar '09     29788 MB  |      3035 MB  |     32823 MB
          Apr '09     40171 MB  |      8148 MB  |     48320 MB
          May '09     12773 MB  |      4538 MB  |     17311 MB
        ------------------------+---------------+---------------
        estimated     24180 MB  |      8591 MB  |     32771 MB





you may just have to keep an eye on it manually and stop the torrents when you get close.

Steve

---

### Post by laffinet on 2009-05-17
My ISP does't have an unmeasured time slot. All traffic gets measured, so that's not an option for me, unfortunately...

---

### Post by jbruced on 2009-05-17
If you can write a small bash script then check this out

[http://tombuntu.com/index.php/2007/08/30/traffic-monitoring-with-vnstat/](http://tombuntu.com/index.php/2007/08/30/traffic-monitoring-with-vnstat/)

run a recuring cron job every so often
grep for the accumulated usage
run a pkill <nameoryourbittorrentclient> when you reach the limit

man vnstat for lots of options 
see the vnstat webite for more details [http://humdi.net/vnstat/](http://humdi.net/vnstat/)

I hope this helps.

---

