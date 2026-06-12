---
title: "[SOLVED] Evince on 1 machine acting weird, rest OK."
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-20
Hi Gang

Is there a place to check the setting for the EVINCE Document Viewer?????

I thought I had a couple of messed up .pdf files because they didn't display right on the main machine I do my work from.

I checked the files on other Ubuntu machines and XP machines and they look and work just fine.

But on this machine, one file when it loads, it comes up with two side by side windows, which it shouldn't do.  And the other file gives the ERROR, Unknown MIME Type!

I had redone both of these files a couple of times before I decided to see what they looked like on the other machines and they worked just fine on every other machine, even olde machines, I loaded the files into.

So my thought is, must be a configuration file somewhere so I can check to see what reads different on this machine than on all the other machines.  Although they were all loaded from the same CD and have had the same updates.

Hardy 8.04 LTS, using Firefox which opens .pdf's in Evince!

TTUL
Gary

---

### Post by squaregoldfish on 2008-12-20
I find evince to be a strange beast that occasionally sulks at an individual file for no reason.

When this happens, I use either the Adobe Acrobat Reader, or KPDF, which also doubles as a PostScript viewer.

To change which program Firefox uses to view these documents, go to Edit -> Preferences -> Applications. Find the PDF entry, and select the program of your choice.

Steve.

---

### Post by Kellemora on 2008-12-20
Hi Steve

I think NOW I have an even more interesting problem!

I checked Edit/Preferences/Applications and it's ALREADY set to "Use Adobe Reader 8.0 (in Firefox)" but it uses Evince anyhow!

I checked all the other machines too while I was at it and they are all set the same way, for Adobe, except one that shows NO .pdf viewer at all, yet the little "e" for Evince comes up in the panel when the .pdf is open.
On the machine where nothing shows, the .pdf brings up the download program and then a window pops up that says, Open With (and the only choice is Document Viewer, which is Evince.)
Evince IS checked in Synaptic on that machine.

Apparently you cannot turn it off, because it removes the Ubuntu Desktop?  

Oh well, I've had stranger things happen!

Thanks for the ideas to try though!

TTUL
Gary

---

### Post by squaregoldfish on 2008-12-21
In your mozilla settings directory (~/.mozilla/firefox/????.default), there's a file called mimeTypes.rdf. It's this file that that contains details of what Firefox does with various files. It seems that my copy contains several different entries for PDFs, so it might be that that's causing you issues.

I don't know how this file works, or what messing about with it will do to Firefox, but if you're feeling adventurous you could try removing all the entries except the one that you want. (I assume you know how XML works - if not, you're better off leaving well alone!)

Steve.

---

### Post by Kellemora on 2008-12-21
HI Steve

I don't even have the slightest inkling of what XML is!
But I did roam around the folders to see what was hidden there.

I have a test machine I don't mind fiddling with things on.
But I found nothing on it to fiddle around with, hi hi.....

All the .pdf files work A-OK on that machine.  It's just this machine that keeps showing the error message.
And what makes that even more interesting is the .pdf file was written ON THIS MACHINE using Open Office then exported as a .pdf file, same as all the other files I made that day.

I've redone this one 5 times now with the same results.
Weird, just Weird, hi hi..........

Oh well, at least the purpose for which I made the files is working, everyone except the AUTHOR can view it no problem, hi hi......

I wonder WHY Adobe is NOT picking these up, since that is what is selected to read .pdf files?

TTUL
Gary

---

### Post by squaregoldfish on 2008-12-22
I think the problem is that the configuration file I mentioned has ended up with two entries for what to do with PDFs, and Firefox gets itself a bit confused. (This is only a guess based on what I saw in my config, so it may or may not be a correct diagnosis.)

If you don't know XML, it's probably best to leave well alone - it's quite easy to break stuff if you get the formatting of the file wrong. However, if you post the relevant file up here, I can have a look at it.

To find the file, open a Terminal and type:

locate mimeTypes.rdf

You'll find a number of matches, and the one you want is:

/home/<username>/.mozilla/firefox/<random letters>.default/mimeTypes.rdf

You can attach this file to the message here, and I'll have a look around.

Steve.

---

### Post by Kellemora on 2008-12-22
Thanks SG

I read the file, see things in it I have no idea what they are doing in there, since I've never done that or been there.  But here you go!

While you're in there, see if you can see WHY midi files stop at Cache Load 0.46% on this machine too.  That's another problem we have never resolved on this particular machine.  But worked on for almost a month with the help of many.  Might be related?

TTUL
Gary

```
root@HPpav753nUbuntu:/home/gary# cat /home/gary/.mozilla/firefox/6vir4klt.default/mimeTypes.rdf
<?xml version="1.0"?>
<RDF:RDF xmlns:NC="http://home.netscape.com/NC-rdf#"
         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
  <RDF:Description RDF:about="urn:handler:web:http://compose.mail.yahoo.com/?To=%s"
                   NC:prettyName="Yahoo! Mail"
                   NC:uriTemplate="http://compose.mail.yahoo.com/?To=%s" />
  <RDF:Description RDF:about="urn:mimetype:audio/midi"
                   NC:value="audio/midi">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:audio/midi"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:webcal"
                   NC:value="webcal">
    <NC:handlerProp RDF:resource="urn:scheme:handler:webcal"/>
  </RDF:Description>
  <RDF:Seq RDF:about="urn:mimetypes:root">
    <RDF:li RDF:resource="urn:mimetype:audio/midi"/>
    <RDF:li RDF:resource="urn:mimetype:application/x-msdownload"/>
    <RDF:li RDF:resource="urn:mimetype:application/pdf"/>
  </RDF:Seq>
  <RDF:Seq RDF:about="urn:schemes:root">
    <RDF:li RDF:resource="urn:scheme:mailto"/>
    <RDF:li RDF:resource="urn:scheme:webcal"/>
  </RDF:Seq>
  <RDF:Description RDF:about="urn:mimetype:application/pdf"
                   NC:value="application/pdf">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/pdf"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:audio/midi"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="false" />
  <RDF:Description RDF:about="urn:mimetypes">
    <NC:MIME-types RDF:resource="urn:mimetypes:root"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:externalApplication:application/x-msdownload"
                   NC:prettyName=""
                   NC:path="" />
  <RDF:Description RDF:about="urn:schemes">
    <NC:Protocol-Schemes RDF:resource="urn:schemes:root"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:handler:mailto"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="false">
    <NC:possibleApplication RDF:resource="urn:handler:web:https://mail.google.com/mail/?extsrc=mailto&amp;url=%s"/>
    <NC:possibleApplication RDF:resource="urn:handler:web:http://compose.mail.yahoo.com/?To=%s"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:mailto"
                   NC:value="mailto">
    <NC:handlerProp RDF:resource="urn:scheme:handler:mailto"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:handler:web:https://mail.google.com/mail/?extsrc=mailto&amp;url=%s"
                   NC:prettyName="Gmail"
                   NC:uriTemplate="https://mail.google.com/mail/?extsrc=mailto&amp;url=%s" />
  <RDF:Description RDF:about="urn:mimetype:application/x-msdownload"
                   NC:value="application/x-msdownload"
                   NC:editable="true"
                   NC:description="">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/x-msdownload"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:root"
                   NC:en-US_defaultHandlersVersion="2" />
  <RDF:Description RDF:about="urn:mimetype:handler:application/pdf"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="false" />
  <RDF:Description RDF:about="urn:scheme:handler:webcal"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="true">
    <NC:possibleApplication RDF:resource="urn:handler:web:http://30boxes.com/external/widget?refer=ff&amp;url=%s"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:application/x-msdownload"
                   NC:alwaysAsk="true"
                   NC:saveToDisk="true">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/x-msdownload"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:handler:web:http://30boxes.com/external/widget?refer=ff&amp;url=%s"
                   NC:prettyName="30 Boxes"
                   NC:uriTemplate="http://30boxes.com/external/widget?refer=ff&amp;url=%s" />
</RDF:RDF>
root@HPpav753nUbuntu:/home/gary#
```

---

### Post by squaregoldfish on 2008-12-27
Hi there,

I haven't forgotten about this, it's just that Christmas is getting in the way a bit. Hopefully I'll have time to look at this in the next week or so.

Steve.

---

### Post by squaregoldfish on 2009-01-06
OK, I've finally got round to looking at your file. I've updated your file with my PDF settings. I've no idea whether or not it will work, but let's give it a go. Use the following steps.

1. Quit Firefox
2. Take a copy of your existing mimeTypes.rdf file (just in case the update breaks!)
3. Install the new file in its place
4. Restart Firefox, and see if PDF handling works

```
<?xml version="1.0"?>
<RDF:RDF xmlns:NC="http://home.netscape.com/NC-rdf#" xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
    <RDF:Description RDF:about="urn:handler:web:http://compose.mail.yahoo.com/?To=%s" NC:prettyName="Yahoo! Mail" NC:uriTemplate="http://compose.mail.yahoo.com/?To=%s" />
    <RDF:Description RDF:about="urn:mimetype:audio/midi" NC:value="audio/midi">
        <NC:handlerProp RDF:resource="urn:mimetype:handler:audio/midi"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:scheme:webcal" NC:value="webcal">
        <NC:handlerProp RDF:resource="urn:scheme:handler:webcal"/>
    </RDF:Description>
    <RDF:Seq RDF:about="urn:mimetypes:root">
        <RDF:li RDF:resource="urn:mimetype:audio/midi"/>
        <RDF:li RDF:resource="urn:mimetype:application/x-msdownload"/>
        <RDF:li RDF:resource="urn:mimetype:application/pdf"/>
    </RDF:Seq>
    <RDF:Seq RDF:about="urn:schemes:root">
        <RDF:li RDF:resource="urn:scheme:mailto"/>
        <RDF:li RDF:resource="urn:scheme:webcal"/>
    </RDF:Seq>
  <RDF:Description RDF:about="urn:mimetype:handler:application/pdf"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/pdf"/>
  <RDF:Description RDF:about="urn:mimetype:application/pdf"
                   NC:description="PDF document"
                   NC:value="application/pdf"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/pdf"/>
  </RDF:Description>
  </RDF:Description>
    <RDF:Description RDF:about="urn:mimetype:handler:audio/midi" NC:useSystemDefault="true" NC:alwaysAsk="false" />
    <RDF:Description RDF:about="urn:mimetypes">
        <NC:MIME-types RDF:resource="urn:mimetypes:root"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:mimetype:externalApplication:application/x-msdownload" NC:prettyName="" NC:path="" />
    <RDF:Description RDF:about="urn:schemes">
        <NC:Protocol-Schemes RDF:resource="urn:schemes:root"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:scheme:handler:mailto" NC:useSystemDefault="true" NC:alwaysAsk="false">
        <NC:possibleApplication RDF:resource="urn:handler:web:https://mail.google.com/mail/?extsrc=mailto&amp;url=%s"/>
        <NC:possibleApplication RDF:resource="urn:handler:web:http://compose.mail.yahoo.com/?To=%s"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:scheme:mailto" NC:value="mailto">
        <NC:handlerProp RDF:resource="urn:scheme:handler:mailto"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:handler:web:https://mail.google.com/mail/?extsrc=mailto&amp;url=%s" NC:prettyName="Gmail" NC:uriTemplate="https://mail.google.com/mail/?extsrc=mailto&amp;url=%s" />
    <RDF:Description RDF:about="urn:mimetype:application/x-msdownload" NC:value="application/x-msdownload" NC:editable="true" NC:description="">
        <NC:handlerProp RDF:resource="urn:mimetype:handler:application/x-msdownload"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:root" NC:en-US_defaultHandlersVersion="2" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:application/pdf"
                   NC:path="/usr/bin/acroread"
                   NC:prettyName="acroread" />
    <RDF:Description RDF:about="urn:scheme:handler:webcal" NC:useSystemDefault="true" NC:alwaysAsk="true">
        <NC:possibleApplication RDF:resource="urn:handler:web:http://30boxes.com/external/widget?refer=ff&amp;url=%s"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:mimetype:handler:application/x-msdownload" NC:alwaysAsk="true" NC:saveToDisk="true">
        <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/x-msdownload"/>
    </RDF:Description>
    <RDF:Description RDF:about="urn:handler:web:http://30boxes.com/external/widget?refer=ff&amp;url=%s" NC:prettyName="30 Boxes" NC:uriTemplate="http://30boxes.com/external/widget?refer=ff&amp;url=%s" />
</RDF:RDF>

```

---

### Post by Kellemora on 2009-01-06
Hi SG

I tried to send you a thank you earlier and to say the file you sent made Adobe show the file instead of Evince in Firefox.

That's good!

But I still have one file that shows up with Unknown Mime Type, even though it was redone 5 times using Open Office exactly the same as the other files were done.
However, it opens just fine on all the other computers!
So it could just be a strange quirk only affecting this computer!

Nonetheless, getting Adobe to respond was what we were after, and your file replacement did the trick!

So I'm marking this solved!

Thank You for your help!

TTUL
Gary

---

