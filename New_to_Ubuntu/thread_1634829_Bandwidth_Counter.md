---
title: "Bandwidth Counter"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Abadon125 on 2010-12-01
Hello, I am running ubuntu server 10.10 with no front end and am looking for a bandwith counter. I have found some good programs that display the current bandwidth usage such as bmon but nothing that will count the total bandwidth used.

Does anyone have any suggestions? Idealy I would love something that can have monthly or daily totals but that is not a requirement.  The only feature I really need is the ability to track how much bandwidth has been used. 

Thanks for the help!

---

### Post by karthick87 on 2010-12-01
**Install vnstat**
```
sudo apt-get install vnstat
```**To start vnstat type the following in terminal**
```
sudo vnstat -u -i <interface>
```(i.e sudo vnstat -u -i eth0)

[B]To see the Bandwidth usage type vnstat  in termina
[/B]```
vnstat
```**Output of vnstat will show you the result,like the one you see below**
> karthick@Ubuntu-desktop:~$ vnstat
Database updated: Wed Dec  1 16:14:45 2010

   eth0 since 11/29/10

          rx:  532.00 MiB      tx:  262.74 MiB      total:  794.73 MiB

   monthly
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
       Nov '10    412.00 MiB |  239.16 MiB |  651.16 MiB |    2.06 kbit/s
       Dec '10    119.99 MiB |   23.58 MiB |  143.57 MiB |   20.11 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated      5.32 GiB |    1.03 GiB |    6.35 GiB |

   daily
                     rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
     yesterday    196.29 MiB |   33.05 MiB |  229.34 MiB |   21.75 kbit/s
         today    119.99 MiB |   23.58 MiB |  143.57 MiB |   20.11 kbit/s
     ------------------------+-------------+-------------+---------------
     estimated       175 MiB |      34 MiB |     209 MiB |


---

### Post by Abadon125 on 2010-12-01
Wow that looks great, thanks.
I don't suppose there is any way to see traffic per port? For example I've got seeding on one port and a game server on another and would love to see how much each takes.

---

