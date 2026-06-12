---
title: "Wifi and Wine Issue"
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by joonwo on 2014-10-10
Hello Ubuntu Community, 
i am new to ubuntu, swiched from windows 2 days ago and i have to say it's quite cool.
 i managed to get everything to work. except one thing...

I use Wine and PlayOnLinux to run Windows Office 2007. It does run quite well. Only Printing is a pain in the a**.
I have a Canon MG5250 WIFI Printer.
i added it through Host and entered the IP of my printer since it couldn't detect it over wifi by itself.

everytime after writing a document i press ctrl + p to open printer setting and press the printing button. but i doesn't seem to do anything in office.
it says printer status Idle in Office and then i check again in Ubuntu and it says printer online.

thanks for your help :)

---

### Post by weatherman2 on 2014-10-10
This isn't really a "WiFi" issue.

It's either a printer issue or a Wine issue.  There is a separate Ubuntu forum for Wine and also Wine itself has a good support forum at [www.winehq.org](www.winehq.org) .

Can you print from Ubuntu itself - from a text editor or just a test page - but only not from Office 2007 via Wine?  If you can print from normal Ubuntu applications but not from Office 2007, then it is likely Wine.  If you can't print from anything from any program, you need to get the printer setup correctly in Ubuntu.

---

### Post by joonwo on 2014-10-10
just tested with libre office, wifi printing seems to work. so must be wine or office07... 

just asking is anyone using MS office (which version?) and can wifi print?

---

### Post by pdc on 2014-10-10
Hi joonwo;

You don't tell us if you use the 32bit or the 64bit variant of ubuntu; 

Can I recommend you install the linux printers that Canon supply to you for free, for your printer? That would allow you to print directly from Ubuntu. To try to cover all bases, Canon supply 6 variants, but also an install script that does the work for you;

If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100301702.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100301702.html?r=s&q=) and click to download and select the SAVE option, you will be getting [COLOR="#008000"]cnijfilter-mg5200series-3.40-1-deb.tar.gz[/COLOR]

____________________

but just before we install that, we need to get a small file called [COLOR="#0000FF"]libtiff4[/COLOR] and install it first: so go here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go 14 down the list; for the 64bit variant (ending in [COLOR="#0000FF"]amd64.deb[/COLOR]) or 18 down (ending in [COLOR="#0000FF"]i386.deb[/COLOR])

You will astutely note the first 14 on the list are [COLOR="#0000FF"]libtiff4-dev[/COLOR] variants ..............and you don't want any of those ...............

If you click on the [COLOR="#0000FF"]libtiff4[/COLOR] you want, your system should offer to download and select the install option if possible ...............
__________________________________

lest you ask why libtiff4 is needed ...............well, ubuntu is more sort of cutting-edge; and they took libtiff4 away at this latest release; more conservative distros such as debian still stock it ........ the latest Canon drivers are version 4.0 and later and they don't need it: you have an older 3.6 as your printer was first released in 2010; as that was when the printer driver was released ............

_______________

if you are happy [COLOR="#0000FF"]libtiff4[/COLOR] is installed, we move to the printer driver

we need to use the terminal [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) > Keyboard Shortcut: Ctrl + Alt + T  if you can deftly use three fingers together .................

to paste into a terminal, use your mouse and the top line of the terminal ie File and then to the right to Edit and down to paste .............

so go right ahead and open a terminal .................

_________________

if you paste the commands below into a terminal; and after each line is pasted; hit the ENTER key ............

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg5200series-3.40-1-deb.tar.gz
cd cnijfilter-mg5200series-3.40-1-deb
./install.sh
[/COLOR]
and that will start the install script; it will ask you for your sudo password; so have that ready;

sounds as though your printer is wireless; key is that the printer is already recognised by your router; sounds as though it is .........so the install script should "see" it and ask you if that is the one to configure

---

