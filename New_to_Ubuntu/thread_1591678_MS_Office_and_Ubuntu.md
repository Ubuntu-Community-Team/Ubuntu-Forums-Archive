---
title: "MS Office and Ubuntu"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by simolokid4 on 2010-10-09
Hi,

I've been searching around about how to get ms office working on ubuntu but the only possiblity i've found so far is installing wine and within wine install office 2007.

The only thing keeping me from a full transfer of OS is that office 2010 isnt supported, and wine + office 2007 simply doesn't do well enough (crashes like 70% of the time).

Another solution would be open-office but I can't tell you how much I hate the looks of tables in office 2010 when ive opened a .odt file in office 2010... Not to mention that I really like the automatic table of contents and heading-style themes in office 2010.

So my question really is,

Did i miss something ? Is there a way to get ms office 2010 working on ubuntu? Since if there is, I'll switch to ubuntu on every goddamn piece of hardware I own within 4 houres.

Not that I hate windows 7, but I simply like Ubuntu better =P

Thanks for any response I can get ;)

Kind regards,

Simolokid

---

### Post by ProntoAnthony on 2010-10-09
Another way to run MS software is to install Windows in a virtual box. Check out VirtualBox. I did after being frustrated with Wine and VMware. It simply works.

-Anthony

---

### Post by hamstermoon on 2010-10-09
I don't know about getting MS Office 2010 working in Ubuntu (I used 2007 in Wine for a while and it was fine).

I hate the new ribbon layout in MS Office so much I even have have Open Office installed on my Windows computers to get me round that problem. Sometimes however I need to use it to render a Word Document / Excel Spreadsheet properly as OOo messes it up. That happens with application forms for jobs a lot. 

The OMG!Ubuntu! blog pointed out a while ago that Sky Drive gives you access  to a cut down version over the internet. Here is the link to the  article.

[http://www.omgubuntu.co.uk/2010/06/microsoft-office-web-apps-now-available-in-the-uk/](http://www.omgubuntu.co.uk/2010/06/microsoft-office-web-apps-now-available-in-the-uk/)

Hope this helps!

---

### Post by ronnielsen1 on 2010-10-09
> The only thing keeping me from a full transfer of OS is that office 2010 isnt supported, and wine + office 2007 simply doesn't do well enough (crashes like 70% of the time).
Well 2010 hasn't been figured out yet but 07 should work great but there's some library overrides that you have to put in

> What works
Everything tested (installer, word, excel, and powerpoint) doing standard operations within each application.

What does not
Nothing that I found.

What was not tested
I didn't go through all features but did run the standard ones.

Additional Comments
Enterprise edition

Had to do the following:

$ winetricks msxml3
$ wine /path/to/setup.exe

Failure to install msxml3 via winetricks lead to the setup.exe crashing upon loading and wine asking me if I wanted to send a crash report to microsoft.  The install completes just fine after this override.  I tested this procedure on three Arch x86_64 machines and can verify that it is indeed needed in all three cases.

You do need to add an override for riched20 (native, builtin) for powerpoint to work, but this is a known issue.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)
There's also seperate links on that page for word, excel etc. If you click on these, it will show you how to get MS Office 2007 running right. It doesn't crash for me. If you're trying to run Windows software google winehq softwareyouwanttorun and you'll find the winehq page you're trying to find.

---

### Post by simolokid4 on 2010-10-09
The virtualbox will probably work for me desktop.

My laptop however, cant virtualize so thats another issue.

I just looked trough the web app and that seems to do the trick for most of the work that has to be done. That only misses the table-styling and automatic table of contents. Ah well, its a cut-down version and it's not like i need to use those functions all that much

Thanks for the answers ;)

sounds like I've got some re-installing to do (Not going to keep up to the 4 houre promise though, since that would give me .. (11.49 + 4 = 3.49 till 8.00 = about 4 houres of sleep for my fathers birthday tomorrow ... thats just not very social.

"Happy bday dad"
"What the hell happend to you?"
"Had a promise and couldnt break it.." =P

I will take a closer look to all the apps I use and triple check if there's something that ubuntu cant replace.

If not, I sure as hell will transer to ubuntu :)

Thanks for all the help again.

Very kind regards,

Simolokid

[ps. i just read ronnielsen1's reaction and will try that first on my laptop asap. If that doesn't work i'll go webapp on laptop and normal virtualbox on desktop :) ]
( I keep thanking u guys so im going to skip that here =P)

---

### Post by SeijiSensei on 2010-10-09
[Crossover Linux]("http://www.codeweavers.com/products/cxlinux/") is a commercial version of Wine that generally provides better compatibility with major Windows applications.  There isn't support for Office 2010 yet ([estimated]("http://www.codeweavers.com/support/tickets/browse/?ticket_id=802501") some time next year); here's the [page describing where things stand for Office 2007]("http://www.codeweavers.com/compatibility/browse/group/?app_parent=1911;").

---

