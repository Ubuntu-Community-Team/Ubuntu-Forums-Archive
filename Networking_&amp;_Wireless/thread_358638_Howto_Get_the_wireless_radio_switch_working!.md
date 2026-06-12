---
title: "Howto: Get the wireless radio switch working!"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Skardal on 2007-02-11
I've just managed to get my ipw2200 wireless card working 100%. The big problem was to get the radio  button working. But now it is! :)

Find your laptop here: [http://rfswitch.sourceforge.net/?page=laptop_matrix]("http://rfswitch.sourceforge.net/?page=laptop_matrix")

In my case I just had to load the "acerhk" module with parameters "poll=1 autowlan=1". 
In the laptop-matrix you can see if you have to set some parameters.

Note: there is no need to download/install acerhk if you are running Edgy(not sure about Dapper and older versions..)! 

I hope this can be to someones help! (At least I know where to find out which parameters to use next time I have to reinstall or upgrade! :roll: )

---

