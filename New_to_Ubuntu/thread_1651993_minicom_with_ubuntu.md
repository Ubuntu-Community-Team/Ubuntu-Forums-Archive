---
title: "minicom with ubuntu"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by superprash2003 on 2010-12-24
i've been trying to use minicom with ubuntu and i've somehow got it to work.. Im trying to create a minicom script but for some reason after the script is done minicom doesnt exit even though i added a line "exit 0" to the script. minicom doesnt exit. i have to manually exit it..
  Anybody knows how to exit minicom automatically while running scripts?Also if anybody knows any alternative application which helps in serial port communication which also supports scripting it would be great..
 THanks...

---

### Post by HermanAB on 2010-12-24
Howdy,

You should try Cutecom for ease of use and Kermit for scripting.

---

### Post by superprash2003 on 2010-12-25
@HermanAB
  thank you so much for your reply.. i did follow your suggestion and tried playing with kermit.. i even created a small kermit script. i got the script to connect to the serial connection. but i need to now pass the string "a" to the connection but im unable to do so.. here is the script so far

#!/usr/bin/kermit +
kermit -l /dev/tty8
set speed 9600
set reliable
fast
set carrier-watch off
set flow-control none 
set prefixing all
connect


after connect.. i need to send string "a" to the connection and then the script should exit itself. would really appreciate any help..thanks..

---

### Post by HermanAB on 2010-12-26
Uhmmm, it is about 25 years since I last used Kermit.  All I can remember is that the help and example files were very good:
[http://www.columbia.edu/kermit/ckscripts.html](http://www.columbia.edu/kermit/ckscripts.html)

---

