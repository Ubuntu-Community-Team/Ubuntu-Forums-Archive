---
title: "Installing ie6/ie7 using wine and proxy settings"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by wstay on 2009-01-09
I install ie6/ie7 using wine with this command:
./ies4linux --hack-ie7-proxy-settings.
After a few moment, it opened ie6 and asked me to configure my proxy settings.
I am not familiar with proxy settings.
Can someone please tell me what proxy settings I should put for ie6 before the installation will continue?

---

### Post by computermacgyver on 2009-01-09
If you do not know proxy settings, they you probably do not need them. Try to just leave the proxy information blank and click ok.

In Ubuntu proxy settings are under System->Preference->Network Proxy . If you have any settings there, you will want to copy them into IE. (My guess if this is a home PC is that you will not have any proxy settings.)

---

### Post by wstay on 2009-01-09
I successfully installed ie6/ie7.
But when I open ie6/ie7 using: wstay@ubuntu8:~/bin$ ie7
It gives me a message: rm: remove write-protected regular empty file `/home/wstay/.ies4linux/ie7/.firstrun'? 
And when I type y for yes, it says: rm: cannot remove `/home/wstay/.ies4linux/ie7/.firstrun': Permission denied
I used my root login with my root password to login to change the permission
(chown wstay and chmod 0777) but also cannot remove write-protected regular empty file `/home/wstay/.ies4linux/ie7/.firstrun
How can I do that?

---

### Post by kestrel1 on 2009-01-09
May seem like a silly question, but why do you want to use IE under Ubuntu?
Firefox or Opera are far better & do not cause problems like this.

---

### Post by porchrat on 2009-01-09
> **wstay said:**
> I successfully installed ie6/ie7.
But when I open ie6/ie7 using: wstay@ubuntu8:~/bin$ ie7
It gives me a message: rm: remove write-protected regular empty file `/home/wstay/.ies4linux/ie7/.firstrun'? 
And when I type y for yes, it says: rm: cannot remove `/home/wstay/.ies4linux/ie7/.firstrun': Permission denied
I used my root login with my root password to login to change the permission
(chown wstay and chmod 0777) but also cannot remove write-protected regular empty file `/home/wstay/.ies4linux/ie7/.firstrun
How can I do that?

Also...why do you have a root login as opposed to running "sudo" when it is needed?...unless I'm misunderstanding.

---

### Post by MaxVK on 2009-01-09
> **kestrel1 said:**
> May seem like a silly question, but why do you want to use IE under Ubuntu?
Firefox or Opera are far better & do not cause problems like this.

Ill field that one - I use IE for web development testing ;)

Max

---

### Post by kestrel1 on 2009-01-10
> **MaxVK said:**
> Ill field that one - I use IE for web development testing ;)

Max
Yes, fair comment Max. Might be easier to setup VirtualBox & install Windows as a virtual machine for that though.

---

### Post by MaxVK on 2009-01-11
This is true, however, I find it a little on the OTT side to fire up an entire virtual machine just to run one program for web testing, when there is the faintest chance that I can just start that program on its own! Its a lot quicker as well!

Max

---

### Post by kestrel1 on 2009-01-11
True enough, if you can get it to run reliably.

---

### Post by wstay on 2009-01-11
> **kestrel1 said:**
> May seem like a silly question, but why do you want to use IE under Ubuntu?
Firefox or Opera are far better & do not cause problems like this.

I cannot view Online Share Trading from my bank even with Firefox (User Agent Switch)
or Konqueror ( Browser Identification).

In Firefox when I clicked on Online Share Trading, it gave me a message:
There is a LIVE QUOTE new version download.
Click OK to continue download.
Click Cancel to cancel download.
When I clicked OK, the page loaded but opened blank. 

In Firefox I did the following settings (using some of the default settings):
Description - Internet Explorer 7 (Windows Vista)
User Agent - Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5) Gecko/2008121622 Ubuntu/8.10 (intrepid) Firefox/3.0.5
App Name - Microsoft Internet Explorer
App Version - 4.0 (compatible; MSIE 7.0; Windows NT 6.0)
Platform - Linux i686
Vendor - Ubuntu
Vendor Sub - 8.10

May be, there are mistakes in these settings.

---

### Post by MaxVK on 2009-01-11
:) Yes, thats true enough - but lets not jack this thread discussing the merits or otherwise of virtual machines - I'm interested in the answer original question myself since I am likely to use this version of IE quite soon.

My apologies to the OP for digressing.

Max

---

### Post by wstay on 2009-01-11
> **porchrat said:**
> Also...why do you have a root login as opposed to running "sudo" when it is needed?...unless I'm misunderstanding.

Oh! Yes, I did use sudo first to changed permission level and when I still could not open IE, I used root for that matter. But it gave me the same problem.
You know what I did. I create a new user with no administrative privilege and then install ie6/ie7. I succeed and can now open ie6 but not ie7.
ie7 is still beta for wine. So I presume it's like that.

---

### Post by kestrel1 on 2009-01-11
Did you follow the instruction [HERE]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu") when you installed IE?
& also apologies for going off thread with VBox.

---

### Post by computermacgyver on 2009-01-11
> **wstay said:**
> 
In Firefox when I clicked on Online Share Trading, it gave me a message:
There is a LIVE QUOTE new version download.
Click OK to continue download.
Click Cancel to cancel download.
When I clicked OK, the page loaded but opened blank. 

In Firefox I did the following settings (using some of the default settings):
Description - Internet Explorer 7 (Windows Vista)
User Agent - Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5) Gecko/2008121622 Ubuntu/8.10 (intrepid) Firefox/3.0.5
App Name - Microsoft Internet Explorer
App Version - 4.0 (compatible; MSIE 7.0; Windows NT 6.0)
Platform - Linux i686
Vendor - Ubuntu
Vendor Sub - 8.10

May be, there are mistakes in these settings.


I do not think there is any problem with the user-agent. Rather I think it is the download aspect. It seems the site will try to download/install some piece of windows software, which naturally will not work on Linux. You might be able to run it successfully under wine as you have been trying with ie6/7 or, you might install Windows firefox under wine and try there. I have had better success getting some sites/applications to work with firefox under wine than with ie. As has been mentioned, another (certainly much bigger footprint) option is to install a virtual environment and run a full virtual copy of windows. Let's hope that this is not necessary just to view this one site.

---

### Post by jackwilson on 2010-11-26
I have to report my work on a website that only works with IE. Not all of the functions of my work website will work on any other browser, and yes I have tried them all. I wish my work site would work on the others, but the web geeks my employer hired probable can't figure out how to get it to work on other browsers. They haven't been able to get this site to work on IE all the time ether .

---

### Post by Mark Phelps on 2010-11-27
> **jackwilson said:**
> I have to report my work on a website that only works with IE. Not all of the functions of my work website will work on any other browser, and yes I have tried them all. I wish my work site would work on the others, but the web geeks my employer hired probable can't figure out how to get it to work on other browsers. They haven't been able to get this site to work on IE all the time ether .

Wine is not the "miracle cure" many make it out to be.  While SOME apps work very well in Wine, IE is NOT one of them.

Then your only workable solution would be to be running MS Windows in Virtualbox and using IE there.

And NEXT TIME, don't hijack an old thread.  Start a new one instead.

---

