---
title: "Cannot open some webpages"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by MHC on 2010-09-26
Hello! This is day 1 of my attempt to change from Windows to Ubuntu. I had  Ubuntu 10.04 LTS pre-installed on my new PC (without Windows!) But I am having trouble opening some webpages - both Firefox and Chrome cannot open the same ones. In Firefox, I get this message:

**"Proxy Error** The proxy server received an invalid response from an upstream server.
 The proxy server could not handle the request *[GET /name/]("http://www.fmrib.ox.ac.uk/fsldownloads/")*.
 Reason: **Could not connect to remote machine: Operation timed out"**
 
Interestingly, some other pages on the main website open normally, and others give this message. 

Any ideas please?

---

### Post by P4man on 2010-09-26
Are you behind a proxy server ? (maybe your ISP?).

Here is some info on the error you are getting:

[http://www.checkupdown.com/status/E502.html](http://www.checkupdown.com/status/E502.html)

If you are sure the problem is not with the site and the same pages load fine on a different machine from your own network, then you may want to try to disable IPv6. Its possible your ISP doesnt implement it correctly. Here is how:

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by MHC on 2010-09-26
I have disabled IPv6 and re-booted, but the problem remains. Well, there are two unrelated websites giving problems - with one, the same problem occurred using Windows, so there's nothing we can do about that. But with the other, it opens fine in Windows on the same network, but still does not open in Ubuntu. The browser worked hard for several minutes, the correct address came up in the address bar, but finally it gave up. Though this time it did not give me the Proxy error message. Rather, it displayed these diagnostics for a while, which unfortunately mean nothing to me: 

var IE5=(document.getElementById && document.all)? true : false; var W3C=(document.getElementById)? true: false; var currIDb=null, currIDs=null, xoff=0, yoff=0; zctr=0; totz=0; function trackmouse(evt){ if((currIDb!=null) && (currIDs!=null)){ var x=(IE5)? event.clientX+document.body.scrollLeft : evt.pageX; var y=(IE5)? event.clientY+document.body.scrollTop : evt.pageY; currIDb.style.left=x+xoff+'px'; currIDs.style.left=x+xoff+10+'px'; currIDb.style.top=y+yoff+'px'; currIDs.style.top=y+yoff+10+'px'; return false; }}  function stopdrag(){ currIDb=null; currIDs=null; NS6bugfix(); }  function grab_id(evt){ xoff=parseInt(this.IDb.style.left)-((IE5)? event.clientX+document.body.scrollLeft : evt.pageX); yoff=parseInt(this.IDb.style.top)-((IE5)? event.clientY+document.body.scrollTop : evt.pageY); currIDb=this.IDb; currIDs=this.IDs; }  function NS6bugfix(){ if(!IE5){ self.resizeBy(0,1); self.resizeBy(0,-1); }}  function incrzindex(){ zctr=zctr+2; this.subb.style.zIndex=zct

Then it stopped completely and said:

"**The connection was reset**
      The connection was reset
The connection to the server was reset while the page was loading.

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.
    *   If you are unable to load any pages, check your computer's network
          connection.
    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.
        
The connection to the server was reset while the page was loading.
    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.
    *   If you are unable to load any pages, check your computer's network
          connection.
    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web."


But, while all this was going on, I opened the same problem page twice in Firefox with Windows.

---

### Post by P4man on 2010-09-26
Im not convinced this is an ubuntu problem, rather than a network/isp problem or a shoddy website. Are you using the same firefox or chrome version on windows?

Can you post the link to the problematic site?

---

### Post by MHC on 2010-09-26
[SIZE=2][COLOR=#c0c0c0][FONT=Arial][/FONT][[FONT=Arial]http://www.bitlifesciences.com/neurotalk2011/[/FONT]]("http://www.bitlifesciences.com/neurotalk2011/") 
[/COLOR][/SIZE]

---

### Post by P4man on 2010-09-26
Indeed, cant access that site under ubuntu either with any browser.  Even wget fails which means they are doing something fishy. I did some googling and found this:
[http://www.the-scientist.com/blog/display/55895/](http://www.the-scientist.com/blog/display/55895/)

Not sure, maybe its a good thing you cant access it. If you are sure the site is valid, shoot them an email.

---

### Post by Paqman on 2010-09-26
Have you tried switching your DNS to something like [Google]("http://code.google.com/speed/public-dns/") or [OpenDNS]("http://www.opendns.com/")?

---

### Post by MHC on 2010-09-26
OK, thanks for all that. The website looked OK in Windows, but maybe I had better do some more investigating.

---

### Post by P4man on 2010-09-26
Yeah the site works fine in windows here too (although it makes me seasick ;) )

The site resolves to  China, not sure if that is where you expect them? Judging by the few things I find on google, it seems to point to some DNS exploit. My guess is the site or DNS has been hacked, or is a scam. 

If not, then at least they did something wrong on their end.

edit btw:
[http://downforeveryoneorjustme.com/http://www.bitlifesciences.com/neurotalk2011/](http://downforeveryoneorjustme.com/http://www.bitlifesciences.com/neurotalk2011/)

They say its "down" to. Really thinking its a DNS hack that makes it show something on windows. Beware.

---

### Post by MHC on 2010-09-26
Wow, this does seem to be fraudulent. Thanks for the warning, and sorry for taking your time.

---

### Post by jmguti on 2010-11-26
Hello,

I have the same problem to acces to a webpage:
[http://www.measy.com.cn/](http://www.measy.com.cn/)

This is not fraudulent. Is a multimedia producer.

Navigators report an error:
Error 101 (net::ERR_CONNECTION_RESET): Error desconocido.

I have ubuntu 10.10 x86_64 in one computer (recently installed with standard options), 10.04 x86_64 in other. I have tried google-chrome, firefox, konqueror, galeon, and always with the same problem. I have no ip filters.

With the same computers and the same net and DNS, the same url work in windows XP and Windows 7 with all the navigators (chrome,firefox,explorer).

That is a webpage with some firmware I want to check sometimes, but I don't want to use Windows 

What a big problem. What a rare problem!

---

