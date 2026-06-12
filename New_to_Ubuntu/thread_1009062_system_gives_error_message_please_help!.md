---
title: "system gives error message please help!"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by oziekhan on 2008-12-12
Dear Friends,

My system showed this error message as given below... There is an arrow with an exclamation mark which says there are 15 updates but when i start the updates.. i get this error message...please help as i am a complete novice.


[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]

---

### Post by jespdj on 2008-12-12
Do what the error message suggests: open a terminal window (Applications / Accessories / Terminal), then type in the following command:
```
sudo dpkg --configure -a
```
Enter your password when it asks for it.

---

### Post by oziekhan on 2008-12-13
Thanks for that!

When I tried to run the updates... I got the message which was something like: "you got broken links" go to "filter"..

where is this filter?

---

### Post by lewac on 2008-12-17
"Broken" is a choice within the listbox located on the left side of the "Synaptic Package Manager" window. after clicking the link that is broken and then "Apply" do a "Reload" to ascertain that the error has actually been removed.

Once you do this you should be able to reinstall. however if the reload throws up failure dialog(s) try removing (completely) similar named packages and then reinstalling.

for example say we have "libmjpegtools0c2a" being listed as broken but a re-install (and/or reload) gives the same error. Do a search on "libmjpeg" and you may have additional packages listed. make a note of them and (completely) remove them. then try reinstalling ("libjpegtools0c2a" first and separately) via a search and apply (you may notice that when you search on that listing other previous listings may no longer exist). you should then have a successful install. finally after this re-install any removed packages that are still listed under a search on "libmjpeg".

---

