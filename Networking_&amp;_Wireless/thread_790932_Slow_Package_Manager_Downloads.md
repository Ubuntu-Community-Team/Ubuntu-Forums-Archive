---
title: "Slow Package Manager Downloads"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by matthewbpt on 2008-05-11
Anytime I try to download anything from the package manager, the download speed is very slow, usually 6000 B/s. I have a fast internet connection and in Firefox get download speeds up to 2 MB/s, but the speeds downloading from Ubuntu repositories using the package manager is so slow its impractical. I tried changing the server in "Software Sources," "Select best server" but it says "No suitable download source found, Check internet connection." Any ideas about what my problem might be? I'm using a wired connection, but i get the same results using the wireless connection, I'm using Hardy on an amd64 based laptop with 2gb RAM and 2.0Ghz dual core processor.

---

### Post by ew16301 on 2008-05-11
It could be due to the recent release of Ubuntu Hardy. I would reccomended changing the server to a local university and see if that helps at all.

---

### Post by matthewbpt on 2008-05-11
Also I'm trying to add the medibuntu repository,
typing  'sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list' in the terminal gives me output:
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
I cant seem to add the repository

---

### Post by davidshere on 2008-08-14
I am also experiencing slow speeds with the medibuntu repository:

```
Need to get 10.6MB of archives.
After this operation, 1090kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://packages.medibuntu.org hardy/free libavutil1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [40.2kB]
Get:2 http://packages.medibuntu.org hardy/free libavcodec1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [1875kB]
Get:3 http://packages.medibuntu.org hardy/free libavformat1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [288kB]         
Get:4 http://packages.medibuntu.org hardy/free libpostproc1d 3:0.cvs20070307-5ubuntu7.1+medibuntu1 [74.9kB]        
Get:5 http://packages.medibuntu.org hardy/non-free libamrnb3 7.0.0.1-0.0+medibuntu1 [139kB]                        
Get:6 http://packages.medibuntu.org hardy/non-free libamrwb3 7.0.0.2-0.1+medibuntu1 [114kB]                        
Get:7 http://packages.medibuntu.org hardy/non-free mencoder 2:1.0~rc2-0ubuntu13+medibuntu1 [3693kB]                
Get:8 http://packages.medibuntu.org hardy/non-free mplayer 2:1.0~rc2-0ubuntu13+medibuntu1 [4350kB]                 
Fetched 10.6MB in 1h3min18s (2784B/s)
```

---

