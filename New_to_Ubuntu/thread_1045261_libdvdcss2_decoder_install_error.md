---
title: "libdvdcss2 decoder install error"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-20
i tried to install the libdvdcss2 decoder for DVD playback.. i followed the following steps...
i opened a terminal and:

i entered
sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) –output-document=/etc/apt/sources.list.d/medibuntu.list   
i got the screen as below:
==========================================================================
--2009-01-20 20:39:14--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `intrepid.list.2'

100%[======================================>] 230         --.-K/s   in 0s      

2009-01-20 20:39:19 (21.0 MB/s) - `intrepid.list.2' saved [230/230]

--2009-01-20 20:39:19--  [http://%E2%80%93output-document=/etc/apt/sources.list.d/medibuntu.list](http://%E2%80%93output-document=/etc/apt/sources.list.d/medibuntu.list)
Resolving \342\200\223output-document=... failed: Name or service not known.
wget: unable to resolve host address `–output-document='
FINISHED --2009-01-20 20:39:24--
Downloaded: 1 files, 230 in 0s (21.0 MB/s)

==========================================================================
 its showing unable to resolve host address and its saying something failed... can some one please help me with this...

---

### Post by Bachstelze on 2009-01-20
Screw Medibuntu, just get the package right from the developers and install it. ;)

```
http://download.videolan.org/pub/libdvdcss/1.2.10/deb/libdvdcss2_1.2.10-1_i386.deb
sudo dpkg -i libdvdcss2_1.2.10-1_i386.deb
```

---

### Post by redseventyseven on 2009-01-20
Somehow the command has got slightly modified (probably by an overzealous auto-correct function in a word processor or something), and double hyphen has been changed to an "en-dash" - see the bit marked in red.

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list [COLOR="Red"]–[/COLOR]output-document=/etc/apt/sources.list.d/medibuntu.list
```

should be

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list [COLOR="Red"]--[/COLOR]output-document=/etc/apt/sources.list.d/medibuntu.list
```

Just to clarify the difference:

- is a hyphen
– is an en-dash (a line the width of a letter n)
— is an em-dash (a line the width of a letter m)

---

