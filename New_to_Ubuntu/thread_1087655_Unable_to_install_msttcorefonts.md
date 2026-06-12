---
title: "Unable to install msttcorefonts"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by kestrel1 on 2009-03-05
I have just done a fresh install of Ubuntu 8.10 & getting things sorted. I thought I would install the Ubuntu-Restricted-Extras of which msttcorefonts is part, but I keep getting this error:
> 
All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
The above is actually from trying to install the fonts via apt-get after failure in synaptic.
I have tried removing with --purge, but I still get the same error when trying to install. Any ideas?

---

### Post by balaknair on 2009-03-05
You could try manually deleting the package from /var/cache/apt/archives and redownload it([http://packages.ubuntu.com/intrepid/msttcorefonts](http://packages.ubuntu.com/intrepid/msttcorefonts)).
That's worked for me in the past with some packages.

---

### Post by kestrel1 on 2009-03-05
Thanks for the reply, but I get the same error when installing from the deb file that I downloaded from the link.
I purged the removal before I tried to install, but this made no difference.
Any other ideas?

---

### Post by balaknair on 2009-03-05
Trawling through launchpad I found this

[https://answers.launchpad.net/ubuntu/+source/msttcorefonts/+question/44122](https://answers.launchpad.net/ubuntu/+source/msttcorefonts/+question/44122)

---

### Post by kestrel1 on 2009-03-05
Yes, I came across that one, but I didn't run all of the commands. It dont think it solved the original problem for the poster. I can try running all the commands tomorrow, as I am now home & on a diferent machine. I think if all else fails, I will either re-install or forget about it, probablt re-install, as it is a fairly fresh install. There may have been a problem during the initial setup, but I can't think what.

---

### Post by Bearly Able on 2009-03-05
OK, I'm sure this is a daft suggestion, but if the rest of your install is OK, can you not just copy and paste the fonts from another machine?  I had a couple of custom fonts I wanted to add, and I found the solution [here]("http://ubuntuforums.org/showthread.php?t=1048114&highlight=installing+fonts").

---

### Post by balaknair on 2009-03-05
I think what worked for the poster was changing the internet proxy settings, and the other person(the chap who was helping the first poster) mentions that the msttcorefonts package would require proxy access to get the fonts. 

I also found this [http://hostechs.com/tag/usrbindpkg-returned-an-error-code-1/](http://hostechs.com/tag/usrbindpkg-returned-an-error-code-1/) which deals with reinstall and purge not working.

@Lesley 
In some cases it could work, but I'm not too sure about MS truetype fonts(for eg: the files that the application downloads are .exe files). Reading through the documentation of msttcorefonts I think the fonts may need to be configured to use defoma(debian fint manager) to display properly under X Windows, and the various associated files are installed to the following locations
[I]var/lib/msttcorefonts
etc/defoma/hints
usr/share/fonts/truetype[/I]

If getting the ttf installed were crucial, yes it would be possible to just copy over files(both the ttf files as well the settings) and paste where appropriate, but I'm not too sure about this.
But then, the underlying problem would still persist(probably).

---

### Post by kestrel1 on 2009-03-05
Yes I am behind a proxy at work, but I get the error when installing the deb. Does the deb need to get access to the Internet to obtain extra files? I have configured the proxy & updates download OK as does anything else that I install via apt-get.
I will have another look in the morning. Maybe I will see something obvious.

---

### Post by stchman on 2009-03-05
I have the Microsoft fonts on my site:

[http://www.stchman.com/tools/MS_fonts/msfonts.tbz](http://www.stchman.com/tools/MS_fonts/msfonts.tbz)

I will assume you downloaded the archive to your desktop.

First create a folder in your fonts folder.
```
sudo mkdir /usr/share/fonts/truetype/microsoft
```

You can decompress the archive into that folder.
```
sudo tar -xvfj ~/Desktop -C /usr/share/fonts/truetype/microsoft
```

Now install the fonts:
```
sudo fc-cache -fv
```

Installed.

---

### Post by kestrel1 on 2009-03-05
Thanks stchman, I will have a go at that tomorrow morning. I will post back if I have problems still or just to say solved :-)

---

### Post by balaknair on 2009-03-05
> Does the deb need to get access to the Internet to obtain extra files?
I think so. From what I could understand, the .deb doesn't contain the fonts- it seems to be (mainly) a collection of bash scripts which download the installers for the fonts(seem to be .exe files), install the fonts to the appropriate folders, and configure defoma(Debian Font Manager) to use these fonts with whatever settings are needed(also part of the msttcorefonts package). 

So the bash script apparently needs to connect to the net(wget is part of the dependencies for msttcorefonts). So I'm guessing it does need proxy access.

Contents of *[COLOR="Black"]postinst.in[/COLOR]*
```
#!/bin/sh
set -e

. /usr/share/debconf/confmodule

db_get msttcorefonts/dldir
LOCALCOPY=$RET

db_get msttcorefonts/savedir
SAVEDIR=$RET

db_get msttcorefonts/dlurl
URLOVERRIDE=$RET

[B]db_get msttcorefonts/http_proxy
http_proxy=$RET
[/B]
if [ -e /usr/share/fonts/truetype/ms-fonts ] ; then
  cp -p /usr/share/fonts/truetype/ms-fonts /var/lib/msttcorefonts/ms-fonts
  rm -f /usr/share/fonts/truetype/ms-fonts
fi

## Content of update-ms-fonts will be concatenated below
```
(Emphasis added)

---

### Post by stchman on 2009-03-05
> **kestrel1 said:**
> Yes I am behind a proxy at work, but I get the error when installing the deb. Does the deb need to get access to the Internet to obtain extra files? I have configured the proxy & updates download OK as does anything else that I install via apt-get.
I will have another look in the morning. Maybe I will see something obvious.

Yes, the msttcorefonts deb I believe accesses sourceforge.net.

---

### Post by brdmb on 2009-03-05
Ok, this is a long shot, but here goes.

Open a terminal and set up your proxy settings as an environment variable using

```
 export http_proxy=http://proxy.server.address:port 
```

then run your 

```
sudo apt-get install msttcorefonts
```

By the way, if you ever need to do any other downloading from the command line at work, you'll need to set the http_proxy environment variable before you do it.  There is a way to set the variable so it gets set up every time you open the terminal, but I forget how to do that...

Good luck!

---

### Post by kestrel1 on 2009-03-06
> **stchman said:**
> Yes, the msttcorefonts deb I believe accesses sourceforge.net.
I think you have just hit the nail on the head & made it click in mine.
Sourceforge.net is filtered by our ISP. This is a school site & the ISP obviously has found or been told about some content that is not acceptable for viewing or use by the students.
I am the Network Manager & they won't even unblock stuff for me, which is a bit annoying.
That would explain why the msttcorefonts won't download, because they are being blocked.
I have used your way to install & this seems to have worked all be it that it doesn't actually show the msttcorefonts package installed, but I am not to bothered about that.
I had to change the > -xvfj
to look like [qoute]-xvf[/quote]
because I was getting an error thrown up & I also had to specify the name in the tar part> sudo tar -xvfj ~/Desktop/msfonts.tbz -C /usr/share/fonts/truetype/microsoft
but apart from that it has worked.
brdmb: thanks for the input with the http_proxy. I found that last night & it was one of the first things I was going to try this morning, which I did, but as the sourcforge site is blocked it wouldn't have any effect. It would have been fine if the site wasn't blocked. I have had it working before, so this block is a recent addition. I am also having problems with Clamwin, which I use on the Windows machines around here, I am hoping they will sort this one though.
Many thanks to one & all.

---

### Post by kestrel1 on 2009-03-09
I have now sorted this problem. Please see this thread: [http://ubuntuforums.org/showthread.php?t=1088515](http://ubuntuforums.org/showthread.php?t=1088515)
Thanks to everyone who tried to help.
Stupid ISP filtering, don't you just love it. :lolflag:

---

