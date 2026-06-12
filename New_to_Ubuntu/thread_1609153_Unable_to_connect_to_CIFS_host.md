---
title: "Unable to connect to CIFS host??"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by pepperwood on 2010-10-30
This message comes up when trying to print a test page to printer from Ubuntu PC that is connected to XP on another PC by USB?? Any assistance would be appreciated. PW

---

### Post by HermanAB on 2010-10-30
See this: [http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

and try to connect to the Windows printer using telnet on port 9100, then look at the error messages that come back to you:
$ telnet windowsipaddress 9100

Also see this:
[http://technet.microsoft.com/en-us/library/cc728404%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc728404%28WS.10%29.aspx)

---

### Post by pepperwood on 2010-10-30
> **HermanAB said:**
> See this: [http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

and try to connect to the Windows printer using telnet on port 9100, then look at the error messages that come back to you:
$ telnet windowsipaddress 9100

Also see this:
[http://technet.microsoft.com/en-us/library/cc728404%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc728404%28WS.10%29.aspx)

Nice site Herman - I'll look into this and see if I can get Linux to work for me. Thank you! PW

---

### Post by arsenalrocks on 2010-10-31
well , did u r problem get solved pepper ? coz even i m facing the ditto same problem.. will go ahead and test the given sol. :P

---

### Post by pepperwood on 2010-10-31
> **arsenalrocks said:**
> well , did u r problem get solved pepper ? coz even i m facing the ditto same problem.. will go ahead and test the given sol. :P

I haven't the foggiest idea of what I'm doing. Hope you get yours set up. PW:confused:

---

