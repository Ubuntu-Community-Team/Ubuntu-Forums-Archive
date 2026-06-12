---
title: "samsung scx-4216f printer driver help"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by juppuk on 2009-02-17
hi i am completly new to linux and im having trouble installing my printer please help im liking linux and hating windows and i dont want to revert back just because of this.

i have a samsung scx-4216f all in one, it goes through a belkin printer server which requires no drivers it self but requires that the drivers of the printer are installed on each computer and that the printer server can find them to work

computer is a laptop acer aspire 5735 using wireless to a router then wired to the print server 
followed this thread still no joy [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

i do know that samsung use a different way to zip up their files. ive learnt so far that to install u need to do it in terminal, so ive used gzip to extract then archive manager to unzip that then dropped the auto run into terminal but almost ever time it says permission denied (i have changed permissions on the folder) or there is an error
this isnt the only way ive unziped the files ive tried without gzip in serveral different ways.
im pretty fluent with windows so im guessing princibles are similar in linux im not a novice with computers so whatever you think can help i will try

---

### Post by juppuk on 2009-02-20
ive sorted it out me self. some people have looked at this post, so either they are seeing how much of a beginner i am or they have a similar issue. so ill tell you how i done it.
1 downloaded the driver
2 using terminal type: gzip -d (name of file)(you can drag and drop the file/folder rather than typing it all in. note the spaces between letters/words etc.
3 using archive manager unzip the folder you get from step 2
4 this is where i struggled, you need to run the autorun file and every time i got permission errors. in terminal type: 
sudo -s
not sure what this does really but it changed username@ubuntu to
root@ubuntu then i ran the autorun file by draging it in. then job done it ran.
im running my printer from a router to a wired belkin print server then to the printer.
go to printer in system and a printer should be listed but it might think its local and not network change the ip address to ://socket192.168.x.xxx (use the print server ip address) my ip address ended in 1.101 but i since found that the stupid print server changed to 192.168.1.20 dont forget the port number which is port:9100 for port 1 and :9101 for port 2. if your not sure what port to use you can type the ip address in firefox and it will show you the set up.
all this was trial and error it took me 4 days looking at dead end forums and questions other people had put forward the sudo thing i dont really know what it does just saw it somewhere and played with it. i may have done it the long way round not sure but any comments on what i found out would be very appreciated.

---

