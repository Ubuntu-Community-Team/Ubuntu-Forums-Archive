---
title: "sleep in script causing many processes to run"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by kkharinarayanan on 2011-05-03
hii
i just wrote a bash script to make me take a break every 20 minutes for two min.
the script will pop up a full screen terminal and display a count down.
i added it to startup and it is working.
but the problem is that after a while of logging in i see a large number of processes running my script in the system monitor
also there are large number of sleep threads too.
this number increases every 20 minutes.
can any body tell me why this is happening?
:confused:
i think it is due to the sleep command i have used , but not sure.


notify-send "Eye Care " \
            "Eye care has started " \
            -i /home/kkhari/eyecare.jpg
while :
do
sleep 1200
gnome-terminal --full-screen --hide-menubar -x dialog --title "Please take a break to heal your eyes" --pause "          Rest for two minutes" 10 40 120
done

---

### Post by DaithiF on 2011-05-03
Hi, from the script you posted I can't see why this would be, ie. it looks fine to me, and I can run it on my machine (11.04) without the process count growing.

to clarify, are you seeing multiple instances of the **eye.sh** process running?  Nothing in that script calls itself, so the only way more than one eye.sh can execute is if something else is launching it periodically.  You haven't got a cron job to run this have you?

---

### Post by kkharinarayanan on 2011-05-06
thanks daitif
crontab was the problem.
i had tried to do this by crontab but it didn't work .
so i just left and forgot to delete the entry
tanks for helping me out

---

