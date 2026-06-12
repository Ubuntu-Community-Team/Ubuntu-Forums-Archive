---
title: "help with pppoe internet connection"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by rob7mm on 2011-01-26
hi everyone
im a total newb so help me out
i just installed 10.10 maverick 
and i cannot get it to recognise my cable internet
the modem is connected by ethernet and i have tryed "$sudo pppoconf" after going through the prompts it comes up with 

" sorry i scanned 1 interface but the access concentrator of your provider does not respond. please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

the internet runs perfectly in windows please help!

---

### Post by robsoles on 2011-01-26
Welcome to UF.

Did it work using PPPOE in Windows? I think it would have just been using an ethernet TCP/IP connection in Windows.

Never mind, I am using 10.04 so I can't be sure what your icons look like. Boot into your 10.10 install and roll your mouse over the icons next to the time in the top right hand corner there, one of the 'tooltip' messages that comes out should relate to networking, have a look under there and see if you can figure out why it isn't connecting to the router in there.

If you can determine whether or not 10.10 has recognised your NIC (ethernet controller in your computer) then it's a good stepping stone to sorting this out for you.

---

