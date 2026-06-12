---
title: "wget hangs when ftp is the scheme in the URL"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by skthetwo on 2011-03-02
I'm using Ubuntu 10.04 LTS 64 bit, Gnome and creating a terminal via Gnome. In that terminal,One of my 3rd party app scripts hangs when it does something like this:

wget [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes) -o myfile
 
It gets the file ok, but just hang.. there is no CPU use.. its almost as if its waiting for some input.

I tried the same command in the terminal and it too gets the file and then hangs.. q, :q, bye doesn't work. I just end up killing it with CNTRL-Z, CNTRL-Z etc.

 So I tried remove the scheme bit ( the ftp:// )from the target file and when I try:

wget hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes -o myfile
 
in the bash session, wget appends a http:// to the file and gets it and terminates.. The app script also continues on when I edit it to take out the ftp:// bit.. 

Is this particular to my configuration or should I report it to the software developer as an error in their shell script ?

---

### Post by The Cog on 2011-03-02
Your script is faulty. See these I tried by hand:```
**wget [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes)**
--2011-03-02 20:03:36--  [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes)
           => `chromosomes'
Resolving hgdownload.cse.ucsc.edu... 128.114.119.148
Connecting to hgdownload.cse.ucsc.edu|128.114.119.148|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /goldenPath/mm9 ... done.
==> SIZE chromosomes ... done.
==> PASV ... done.    ==> RETR chromosomes ... 
No such file `chromosomes'.

```So: no such file - FTP won't succeed. However, wget didn't hang for me, it exited cleanly.
```
**wget [http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes](http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes)**
--2011-03-02 20:03:50--  [http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes](http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes)
Resolving hgdownload.cse.ucsc.edu... 128.114.119.148
Connecting to hgdownload.cse.ucsc.edu|128.114.119.148|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/](http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/) [following]
--2011-03-02 20:03:50--  [http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/](http://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/)
Reusing existing connection to hgdownload.cse.ucsc.edu:80.
HTTP request sent, awaiting response... 200 OK
Length: 5828 (5.7K) [text/html]
Saving to: `chromosomes'

```For http, chromosomes does exist. But it isn't a real file, it's a directory listing from the web server. You can type the url into your browser to see it.

---

### Post by skthetwo on 2011-03-04
I apologize for wasting your time - the correct command in the shell script and the one I tried out and both of which hang was:
wget [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz) -O myfile

meaning there IS an actual file name in the source file-specification, its not a directory specification. This it downloads and then just sits there at the end, doesn't return to the $( bash) prompt when executed in a terminal session. Sorry for misleading you.This is what it looks like in my terminal:

$ wget [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz) -O myfile
--2011-03-04 14:24:01--  [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz)
           => `myfile'
Resolving hgdownload.cse.ucsc.edu... 128.114.119.148
Connecting to hgdownload.cse.ucsc.edu|128.114.119.148|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /goldenPath/mm9/chromosomes ... done.
==> SIZE chr17.fa.gz ... 30121212
==> PASV ... done.    ==> RETR chr17.fa.gz ... done.
Length: 30121212 (29M) (unauthoritative)

100%[======================================>] 30,121,212   318K/s   in 2m 19s

---

### Post by The Cog on 2011-03-05
Well, that command worked for me. It took just a few seconds longer, and exited properly. So I don't think there is anythong wrong with either wget or with the server you are downloading from. Which leaves the network between them. FTP works by opening two connections - first a control connection is opened and the GET commend is sent over this. Then a second connection is opened to transfer the data. Once the data has finished, the control connection is used again to say it's finished. But while the data is transferring, the control connection is idle. I wonder if there's a NAT translation or a firewall in the way somewhere that is timing out and dropping the control connection, so they can't formally finish the transfer request. If that's the case, I can see no option except to use http instead. Http does it all on one connection so the problem doesn't arise. And in this case, the server does also supports http. So I think you should edit the script and convert ftp to http.

---

### Post by skthetwo on 2011-03-06
yes, regarding the actual application issue at hand I switched to using http: and moved on in doing what I really wanted to do.

But now I'm intrigued by the systems issue - I tried the same wget of the same file on a 32bit Ubuntu,  also connected to the world via my laptop which goes to the router on wifi, also via laptop --(using NX client over wifi)-->64 bit Ubuntu ---(over hardwired ethernet)-->router ---> the world  and they all hang.

But... progress - it seems to be a file size issue. If I download smaller files, the wget terminates and returns to the $ prompt.. At the same site here are two examples - a 200 Kb file and a 2 Kb file

karve@lenovo:~$ wget -v [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17_random.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17_random.fa.gz) -O myfile.txt
--2011-03-06 13:16:28--  [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17_random.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17_random.fa.gz)
           => `myfile.txt'
Resolving hgdownload.cse.ucsc.edu... 128.114.119.148
Connecting to hgdownload.cse.ucsc.edu|128.114.119.148|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /goldenPath/mm9/chromosomes ... done.
==> SIZE chr17_random.fa.gz ... 173198
==> PASV ... done.    ==> RETR chr17_random.fa.gz ... done.
Length: 173198 (169K) (unauthoritative)

100%[======================================>] 173,198      257K/s   in 0.7s    

2011-03-06 13:16:32 (257 KB/s) - `myfile.txt' saved [173198]
karve@lenovo:~$ 

And for the 2Kb file
:

karve@lenovo:~$ wget -v [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/README.txt](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/README.txt) -O myfile.txt
--2011-03-06 13:18:39--  [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/README.txt](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/README.txt)
           => `myfile.txt'
Resolving hgdownload.cse.ucsc.edu... 128.114.119.148
Connecting to hgdownload.cse.ucsc.edu|128.114.119.148|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /goldenPath/mm9/chromosomes ... done.
==> SIZE README.txt ... 2354
==> PASV ... done.    ==> RETR README.txt ... done.
Length: 2354 (2.3K) (unauthoritative)

100%[======================================>] 2,354       --.-K/s   in 0.02s   

2011-03-06 13:18:40 (141 KB/s) - `myfile.txt' saved [2354]

karve@lenovo:~$

---

### Post by The Cog on 2011-03-06
> But now I'm intrigued by the systems issue 
Yes, it's intriguing. But as I say, my guess is a NAT or firewall inactivity timeout on the control connection. Which would be affected by the size of the data file of course. A good wireshark trace should confirm it, but it'll be a big capture file.

---

### Post by skthetwo on 2011-03-07
Thanks for the suggestion about wireshark ! I remember putting data analyzers on the wires many moons ago - things have moved on haven't they.. Anyway I did a capture of the packets for both the BIG file that "hangs' and the small file that doesn't. Not sure what to look for though. Ideas ?

Separately, more progress - turns out that the big file download WILL terminate, 15 minutes later, though.. Basically, it gets the file.. hangs for 15 minutes and then does some sort of retry and then terminates.. Here's the output. Note that delay between 11:24 when to all intents and purposes its got the file and it just hangs until 11:39 when it does a cursory retry and terminates to the $ prompt.

~$ wget [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz) -O myfile.tmp
--2011-03-07 11:23:31--  [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz)
           => `myfile.tmp'
Resolving hgdownload.cse.ucsc.edu... 128.114.119.148
Connecting to hgdownload.cse.ucsc.edu|128.114.119.148|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /goldenPath/mm9/chromosomes ... done.
==> SIZE chr17.fa.gz ... 30121212
==> PASV ... done.    ==> RETR chr17.fa.gz ... done.
Length: 30121212 (29M) (unauthoritative)

100%[======================================>] 30,121,212   463K/s   in 80s     
[COLOR=DarkOrange][ SKTHETWO's annotation.. It hangs here for 15 minutes before displaying the rest ][/COLOR]
2011-03-07 11:24:51 (368 KB/s) - Control connection closed.
Retrying.

--2011-03-07 11:39:53--  [ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz](ftp://hgdownload.cse.ucsc.edu/goldenPath/mm9/chromosomes/chr17.fa.gz)
  (try: 2) => `myfile.tmp'
Connecting to hgdownload.cse.ucsc.edu|128.114.119.148|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /goldenPath/mm9/chromosomes ... done.
==> SIZE chr17.fa.gz ... 30121212
==> PASV ... done.    ==> REST 30121212 ... done.    
==> RETR chr17.fa.gz ... done.

100%[+++++++++++++++++++++++++++++++++++++++] 30,121,212  --.-K/s   in 0s      

2011-03-07 11:39:53 (0.00 B/s) - `myfile.tmp' saved [30121212]

karve@thermaltake:~$ 

btw, thanks for taking an interest.

---

### Post by The Cog on 2011-03-09
My guess is that the first download fails because something timed out the control connection so it couldn't close cleanly at the end. Later, it retries and succeeds becaue the rerty is very fast - all the data is actually there (hence a line of +++ instead of ===).

At the end of the control connection, I guess there should be an exchange saying something like the transfer is completed. 

Chuckle - yes it's a step up from the old serial data analysers. 

You should be able to right-click one packet of the control connection and choose "Follow TCP Stream" to make the diaplay filter those packets and display the entire conversation in a popup. Look at a succesful small download to see what is normal. Don't forget to clear the display filter afterwards or you won't ever see anything else.

A proper connection close should end with an exchange of packets with the FIN (finished) flag set, one in each direction. My guess is that the long download is missing the final message exchange and that the FIN exchange doesn't go right either - as though the far end just stops responding, or perhaps a premature RST (reset) packet from the server.

---

### Post by skthetwo on 2011-03-14
I do connect to the world via a DLINK router and so I thought an easy to do test was to just plug the broadband connection directly into the PC.
wget terminated just fine, in the one test I tried ! 

I'll start looking at the packets in the different execution attempt to see what's different at the end. I'll also try and repeat that direct connection into PC experiment but if it is repeatable then we have more progress.

---

### Post by skthetwo on 2011-03-16
As my previous post mentioned, wget worked just fine with a direct connection from the broadband modem into the PC..

So the suspicion was it was the DLINK DIR-615 router. I had a Trendnet Router lying around so I plugged that in instead and again wget completed just fine !

So, I changed the firmware in the DLINK DIR-615 Rev C1 router to dd-wrt ( the opensource  firmware ) and again wget terminated just fine with no hangs..

So I'm comfortable that the problem was the firmware in the DIR-615 router. Which aspect ? Pass... I'd turned off SPI, DNS caching, even put my PC in the DMZ no luck.

I really needed this wget to work - I have some really large files to download.

O by the way, when previously it waited 15 minutes and retried and terminated, the downloaded files, which were .gz files were regarded by the archive manager as corrupt so that wasn't an option.

---

### Post by ThinClient on 2011-11-30
from: [http://www.gnu.org/software/wget/manual/html_node/Download-Options.html](http://www.gnu.org/software/wget/manual/html_node/Download-Options.html)

/snip

‘-T seconds’
‘--timeout=seconds’
    Set the network timeout to seconds seconds. This is equivalent to specifying ‘--dns-timeout’, ‘--connect-timeout’, and ‘--read-timeout’, all at the same time.

    When interacting with the network, Wget can check for timeout and abort the operation if it takes too long. This prevents anomalies like hanging reads and infinite connects. The only timeout enabled by default is a 900-second read timeout. Setting a timeout to 0 disables it altogether. Unless you know what you are doing, it is best not to change the default timeout settings.

    All timeout-related options accept decimal values, as well as subsecond values. For example, ‘0.1’ seconds is a legal (though unwise) choice of timeout. Subsecond timeouts are useful for checking server response times or for testing network latency. 

/snip

Not sure how to go back to check if the download is corrupt or whole, but my hang events usually have occured after downloading a 30 MB or larger file. The transfer looks complete reporting 100% download and complete. (Via C7 1 GHz processor TinyCore linux running in RAM, wired connection to Cable modem to the net)

I am using GNU WGET 1.13 built on Linux-gnu taken from the tinycorelinux repository on 2011-11-29.

---

### Post by ThinClient on 2011-11-30
Your magic 15 min number is within the snip, as 900 seconds default timeout.

---

