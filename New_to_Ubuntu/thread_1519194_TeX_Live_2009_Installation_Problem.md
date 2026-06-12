---
title: "TeX Live 2009 Installation Problem"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by JMcCYoung on 2010-06-27
I've been using TeX for a number of years on OS X and about a year ago successfully installed TeX Live 2007 on a Thinkpad using Synaptic. I recently got a new laptop, an Acer Aspire 1810TZ that came with Win7 and I immediately installed Lucid on it and in general the system has been very well-behaved. I decided to try to install TeX Live 2009 on it and have been unable to get it to work despite two attempts via the [Quick Install]("http://www.tug.org/texlive/quickinstall.html") directions at TUG.org, and once via Synaptic, with uninstalls in between.

Each time the installation appears to be successful, but when I attempt a test file, I get the following error:


john@1810TZ:~$ latex sample2e.tex
warning: kpathsea: configuration file texmf.cnf not found in these directories: /opt/texlive/2009:/opt/texlive/2009/texmf/web2c.
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009)

kpathsea: Running mktexfmt latex.fmt
warning: kpathsea: configuration file texmf.cnf not found in these directories: /opt/texlive/2009:/opt/texlive/2009/texmf/web2c.
/usr/local/texlive/2009/bin/x86_64-linux/mktexfmt: 983: /texconfig/tcfmgr: not found
fmtutil: config file `fmtutil.cnf' not found.
I can't find the format file `latex.fmt'!

***

On the advice of a couple of sites I went to, I also ran texhash, which produced this message:

john@1810TZ:~$ texhash
warning: kpathsea: configuration file texmf.cnf not found in these directories: /opt/texlive/2009:/opt/texlive/2009/texmf/web2c.

***

I'm assuming I've neglected to do something or done something wrong, but I don't know what. After the installation I added these lines to my .profile, as per the [instructions at TUG]("http://www.tug.org/texlive/doc/texlive-en/texlive-en.html") (3.4.3, on Environment variables for Unix, for bash, with changes for my installing version 2009 on 64-bit Linux):

 PATH=/usr/local/texlive/2009/bin/x86_64-linux:$PATH; export PATH 
  MANPATH=/usr/local/texlive/2009/texmf/doc/man:$MANPATH; export MANPATH 
  INFOPATH=/usr/local/texlive/2009/texmf/doc/info:$INFOPATH; export INFOPATH

***

I'm hoping some kind soul here will take pity on me and offer advice. I'm pretty good at following instructions but poor at troubleshooting this kind of thing.

---

### Post by Sonsum on 2010-06-27
Try the instructions found on this site: [http://ubuntu-manual.org/getinvolved/editors]("http://ubuntu-manual.org/getinvolved/editors")

They're written for people installing texlive to work on the Ubuntu manual, but it sounds like it would fix your problem too.

---

### Post by JMcCYoung on 2010-07-01
> **Sonsum said:**
> Try the instructions found on this site: [http://ubuntu-manual.org/getinvolved/editors]("http://ubuntu-manual.org/getinvolved/editors")

They're written for people installing texlive to work on the Ubuntu manual, but it sounds like it would fix your problem too.

Apologies for taking so long to respond, but life intervened.

Unfortunately, the instructions were essentially the same as what I had done before and I wasn't optimistic. Just in case though, I uninstalled again and reinstalled with the only difference being that as suggested I checked the option to install symlinks. After installation I got the same "Welcome to TeX Live" message I'd gotten before, but even after adding:

PATH=/usr/local/texlive/2009/bin/x86_64-linux:$PATH; export PATH

to my ~/.bashrc file and saving and closing and doing source ~/.bashrc in Terminal it still didn't work:

john@1810TZ:~$ latex sample2e
warning: kpathsea: configuration file texmf.cnf not found in these directories: /opt/texlive/2009:/opt/texlive/2009/texmf/web2c.
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009)

kpathsea: Running mktexfmt latex.fmt
warning: kpathsea: configuration file texmf.cnf not found in these directories: /opt/texlive/2009:/opt/texlive/2009/texmf/web2c.
/usr/local/texlive/2009/bin/x86_64-linux/mktexfmt: 983: /texconfig/tcfmgr: not found
fmtutil: config file `fmtutil.cnf' not found.
I can't find the format file `latex.fmt'!

***

If no one else here has further suggestions I'll try at comp.text.tex or texhax; I was hoping to get help here though because that group and list aren't always as kind to newbies.

Thanks again!

---

### Post by mousomer on 2010-07-01
It might help if you use synaptic (or apt-get) to install texlive 2009. It is now in the Lucid packages.

---

### Post by JMcCYoung on 2010-07-01
> **mousomer said:**
> It might help if you use synaptic (or apt-get) to install texlive 2009. It is now in the Lucid packages.

::sigh:: Yes, you'd think that would work, wouldn't you? I did (as I mentioned in passing in my original post, although it was easy to miss). I was delighted to discover that the repository had been updated from TL 2007 to TL 2009 with Lucid after I'd tried using the command line installer, so I uninstalled that first attempt and then used Synaptic, thinking if *anyone* would know where to put files and symlinks and that sort of thing it would be Synaptic. But unfortunately that install - despite apparently going without a hitch - didn't work either and I got the same error messages about latex.fmt and other critical files not being found.

I have the feeling someone, somewhere, must know some magic command line way to diagnose the problem, and then when provided with the results of those will know the similarly magic commands to fix it.

Thank you for the suggestion though!

---

### Post by Sonsum on 2010-07-02
> **JMcCYoung said:**
> Apologies for taking so long to respond, but life intervened.

Unfortunately, the instructions were essentially the same as what I had done before and I wasn't optimistic. Just in case though, I uninstalled again and reinstalled with the only difference being that as suggested I checked the option to install symlinks. After installation I got the same "Welcome to TeX Live" message I'd gotten before, but even after adding:

PATH=/usr/local/texlive/2009/bin/x86_64-linux:$PATH; export PATH

to my ~/.bashrc file and saving and closing and doing source ~/.bashrc in Terminal it still didn't work:

john@1810TZ:~$ latex sample2e
warning: kpathsea: configuration file texmf.cnf not found in these directories: /opt/texlive/2009:/opt/texlive/2009/texmf/web2c.
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009)

kpathsea: Running mktexfmt latex.fmt
warning: kpathsea: configuration file texmf.cnf not found in these directories: /opt/texlive/2009:/opt/texlive/2009/texmf/web2c.
/usr/local/texlive/2009/bin/x86_64-linux/mktexfmt: 983: /texconfig/tcfmgr: not found
fmtutil: config file `fmtutil.cnf' not found.
I can't find the format file `latex.fmt'!

***

If no one else here has further suggestions I'll try at comp.text.tex or texhax; I was hoping to get help here though because that group and list aren't always as kind to newbies.

Thanks again!

Did you run the script included on that site? It checks for dependencies. There was a lot that I had been missing.

---

### Post by JMcCYoung on 2010-07-12
> **Sonsum said:**
> Did you run the script included on that site? It checks for dependencies. There was a lot that I had been missing.

Again, apologies for the delay in response, and thanks to Sonsum and mousomer for their suggestions. 

In answer to the former, no, I didn't run the script because I didn't register with the Ubuntu manual project because I thought it wouldn't be appropriate to do so when I didn't intend to work on it - although now that I have semi-solved the problem I might, despite my clear ignorance.

I did some more research and after my 6th attempt with TeX Live 2009 I ran across something suggesting that TL 2009 had installation problems that were fixed in [the 2010 pre-test version]("http://www.tug.org/texlive/pretest"). I followed the instructions at that page to download and install it using the GUI Wizard, and then followed the [PATH-setting directions]("http://www.tug.org/texlive/doc/texlive-en/texlive-en.html#x1-340003.4.3") in Karl Berry's TeX Live Guide (altered for my 64-bit build), restarted the computer, fired up [Gummi]("http://gummi.midnightcoding.org/") and it correctly set the default sample the program is supposed to display on start-up. I then ran latex small2e in Terminal and the .dvi I expected was produced.

If I had fully solved the problem as stated I would mark the thread as such, but since I only found a workaround (of sorts) I will leave it as-is but hope others with my problem will find it helpful. Fortunately its usefulness should be fairly brief since I believe TL 2010's full release is due out in just a few months.

Thanks again!

---

