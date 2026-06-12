---
title: "PDF email attachments appear corrupted to correspondents"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Lorin Ricker on 2010-12-08
Ubuntu/Studio 10.4, Thunderbird 2.0.0.24, Ooo 3.1.1

I've been sending .PDF files of documents to other folks by email for years now... only recently has this problem shown up, with increasing frequency:

When I produce a document in Ooo Write to send to a correspondent by email, I use the "Export directly as PDF" button to create/save a .pdf file-version of the doc.  I then drag-&-drop it into a Thunderbird-created email, as an attachment.  This has been working -- that is, the receiver of my email has been able to open & read the .pdf document just fine -- for years.

However, recently I'm getting complaints from several correspondents (typically Win and/or Mac users) that "The file you sent me is corrupted/unreadable..." -- often they'll include the text of the message as they're seeing it; here's an example:

```

[COLOR=#1f497d][FONT=&quot]This is how I received it.[/FONT][/COLOR]
  [COLOR=#1f497d][FONT=&quot]Sam[/FONT][/COLOR]
  
    **[FONT=&quot]From:[/FONT]**[FONT=&quot] Lorin Ricker [mailto:Lorin@xxx.com] 
**Sent:** Tuesday, December 07, 2010 4:41 PM
**To:** "Sam"
**Subject:** Re: "topic"
**Importance:** High[/FONT]
  
   
  %PDF-1.4 %Ã¤Ã¼Ã¶ÃŸ 2 0 obj <> stream xœ*WIËÛ@
 ½çWø\p:’QæîÐI”ç(ld0¡ [FONT=&quot][/FONT]bHI&#8209;0jÂP¹+-‘èõY8Ñ•`I1—oÓšIÄ©{¸v
 *æ.`ÙÆMUq¸Jà,ñ†iÀ¿b£&œ˜vMTPÀNÏR/µ¤ÑÖðS/™ÁóûS¬¢ª6êYå‹m ë1¯*Š)˜
éåÅyÙhi©K‹U!Vu´Ç¤ŸúS•-ý!èÓE„du„GVñBŒ·ÈŒù©äücæ‹à¶ÂT›8¶UƒjQÜ0o™²;»
T‰˜DÍÀsE-ÃfK¿xPÎÆõfèrHÒUhKKá,1”*Ö"Ò¤Æ8E»õÌ~ZtÆð"ìøSDI¤§É8™ÓÌx¾
#î°›Öe»àyr¥DV)Td:æ11eÖ&ÅÈ3³K˜®ü,:&çÔ!¤°écë:‹*Â»Í‚¿Ûº³¤R-›© 
  Íò¿Åçå    !»Kk>¸º)*·À“*>¾~Vèàwþ§X5Ïÿ(N·½2*¿Í~[FONT=&quot][1][/FONT][FONT=&quot][/FONT]Ñ
< endstream endobj 3 0 obj 933 endobj 5 0 obj <> stream xœÔ¼y
`ÜÔµ?~ï•4Òìš}õŒfÑ,žÕ&#8209;íqœX‰íì!†lvÀØYÈ[FONT=&quot][1][/FONT]¡±M$b–âqÙJ $¡emœ'@

%<--snip-->%  ...and so on

```I can indeed (re)read my .pdf file in Evince Document Vierwer (2.28.1) with no problem.  What's going on here?

1.  Is Open Office Write producing invalid .pdf document files?

2.  Is Thunderbird somehow messing up "file attachment" rules, formats?

3.  Has something else (something subtle) changed in the Ubuntu environment that I don't know about?

4. Is the problem "on the other end" and out of my control -- that various versions of Windows and/or Mac email clients have "forgotten" (simultaneously) how to open a simple .pdf attachment?

Is anyone else having similar problems -- anything I can do to fix and recover the ability to confidently send .pdf file attachments via email so that users on other systems can reliably read them?

TIA
  -- Lorin

---

### Post by Lorin Ricker on 2010-12-15
Bump?  No one else is seeing this problem?

It turns out that "a few" of my correspondents have been able to open the problem .PDF files in Win & Mac, and even one on an Android phone.  Others cannot -- whether that's user-error, a failing on their system, or a failing in the way I'm generating &/or attaching the .PDF to an email, I cannot yet say.

Any response for comparison would be appreciated... I'm just looking for clues right now.  This is frustrating, because attaching .PDF files "just used to work" -- reliably -- for all my correspondence.

TIA -- Lorin

---

### Post by eyekone on 2011-03-03
I have the same problem and as you mentioned, this has only happened recently. I first though it would be a Mac problem as the only people who couldn't open the documents had the new Macbooks. Sometimes the message doesn't even get through due to a file being corrupt (depending on the server).

The created PDFs are not only the ones created by OpenOffice with the Export to PDF option, but also those created with Sane from a scanner.

I tried to find a solution by changing programs to create PDFs, but they are still corrupt. 

It's hard for me to test, because I have no possibilities to check on other OS.

Sorry I can't help further, but I believe the more information you have the easier it is.

---

### Post by grahammechanical on 2011-03-03
I have some PDF files that I created using the Open Office Export directly as PDF option. I have just tried to open one with Text Editor and the program refuses to open the document.

I then tried with Notepad and it does open and it shows the same kind of text as you show in your post.

My guess would be that your correspondents are not opening the PDF documents in a PDF viewer or their operating systems have the wrong program set as the default program to open PDF documents.

Regards.

---

### Post by eyekone on 2011-03-03
>grahammechanical
I thought the same thing, however the e-mail server recognise the files as corrupt as well. This probably means that it is not a reader problem.

---

### Post by Lorin Ricker on 2011-03-04
Thanks for the responses!  My own experiences with other users since posting this last December tell me that:

a) Certain correspondents continue to see this problem -- but others do not, and they're receiving the same email with the same .PDF attachment.

b) I'm pretty sure now that it's not the application program which produces the .PDF file which is causing the problem, but instead, it's likely the way it's being attached to the email by the email client program (in my case, Thunderbird).  Did they break something in recent updates?  Or do other email clients cause the same/similar problem?

c) I'm not surprised if some text editor programs would refuse to open a .PDF file "in the raw", as it's pretty close to a binary-format file (with readable text interspersed with formatting commands) -- it'd look pretty much like garbage if the text editor (like Notepad) actually does read it into its edit-buffer.  Some editors limit "line size" or other data-length attributes, and choke if the text-file is "too big" in some dimension -- others just read the whole file into memory without problem.

I think we're onto a subtle email attachment problem -- I just wish I know who to report it to...  Thanks again for the corroborating feedback.  Least I know now that I'm not crazy! ;-)  -- Lorin

---

### Post by mikechant on 2011-03-04
Have you tried using the 'attach file' facility in Thunderbird instead of dragging and dropping? This might offer some additional options as well. (I'd have a look but I'm not at my Ubuntu PC at present)

---

### Post by Lorin Ricker on 2011-03-04
> Have you tried using the 'attach file' facility in Thunderbird instead  of dragging and dropping? This might offer some additional options as  well.

Hmm... No, I hadn't thought of that -- creature of habit, I guess.  Yes, I'll give this a try; at least it might exercise a different code-path, which might help uncover or prove our suspicion of a bug in Tbird.

Is anyone having the *same problem* with a *different* email client, like Evolution, etc.?

---

### Post by melcior on 2011-03-30
I use attach instead drag and drop and the same problem occurs. Not only  pdf are in trouble also ppt and some times doc files . My feeling something is wrong in the new thunderbird. Before update everithing was ok.

---

### Post by kalyp on 2011-05-17
Same problem here. If I read the pdf from my webmail client it's fine, from thunderbird (IMAP) it's corrupted (whether I save it first or try to open it directly). And fwding the email to someone else, he can't open it either. It appears that thunderbird somehow corrupts the file...
I haven't found much around the forums so if someone has a solution, I'm interested!!

---

### Post by Lorin Ricker on 2011-05-17
Does anyone know how to report/escalate this problem to the right Thunderbird developer/maintainers in the Mozilla organization or community?  There seems to be a consensus here that this is a TB problem, not something with Ubuntu, Linux or another program, or even with a correspondent's own email setup.

I've looked around on Mozilla.com (etc.), and haven't found the right way to report this as a serious bug or problem report.  Does anyone else know how to productively and correctly communicate with the Mozilla developer community?  How can we get this problem fixed?

TIA,
-- Lorin

---

### Post by Matbro on 2011-06-01
Hi

I have had probably the same problem both sending and downloading pdf:s

I noticed that after doing a fresh install of Natty 11.04 64 bit and Thunderbird 3.x everything was working normally, sending and receiveing pdf:s as they should.
(the problem was in earlier ubuntu versions as well)

Suddenly today receiving 2 pdf emails from my mobile operator, T-bird corrupts the attachments. I can still open them in my webmail.

Found out in Thunderbird / Edit / Preferences / attachments there are 2 lines telling Thunderbird how to cope with pdf attachments. 
One line saying something about PDF document application/moz-deleted:-pdf open with acroread
The other line saying PDF document application/pdf:.pdf Adobe Reader 9

I deleted the first line (choose Delete Action) and now my T-bird is at least receiving (and actually can read the earlier corrupted pdf attachments in the emails).

Maybe this can be to any help !
Regards
Mats

---

### Post by rtb on 2011-06-23
I'll join the "me too" chorus here.  Thunderbird 3.1.10 on Ubuntu 10.04 connecting to an IMAP server.

PDF attachments will be corrupted but only occasionally -- it is definitely intermittent.  More specifically, the PDF file is truncated, in one case by about 5 kB.  

If I retrieve the PDF through the provider's web mail, I can open it without any problem.

I don't currently see any bugs on Launchpad for Lucid Lynx that look like this.  I'm not sure whether a bug report on something like this would even be welcome any longer for 10.04.

---

