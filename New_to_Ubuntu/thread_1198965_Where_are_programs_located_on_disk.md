---
title: "Where are programs located on disk?"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by drdave69 on 2009-06-28
I am trying to install a Scribus template, it says to extract it in the ~/.scribus/templates folder. I can not find this folder on my computer. Can someone please show me?

---

### Post by swisstone198 on 2009-06-28
Click show hidden files in the "view" menu

---

### Post by drdave69 on 2009-06-28
> **swisstone198 said:**
> Click show hidden files in the "view" menu

Thank you.

---

### Post by drdave69 on 2009-06-28
Still can not find the right folder. I goto Home then click on show hidden files, I see the .scribus folder, but there is no template folder in there. I created on & put the template file there, but scribus does not recognize it when I try to use the template.

---

### Post by drdave69 on 2009-06-28
can anyone show me the correct path please?

---

### Post by s.fox on 2009-06-28
Hi,

You could try a search for it.  [Here]("https://help.ubuntu.com/community/FindingFiles") is some documentation that will help.

-Ash R

---

### Post by owenll on 2009-06-28
You could use the terminal:

```
 **whereis scribus**
scribus: /usr/bin/scribus /usr/lib/scribus /usr/share/scribus /usr/share/man/man1/scribus.1.gz

```

---

### Post by niteshifter on 2009-06-28
Hi,

/usr/share/scribus/templates

---

### Post by drdave69 on 2009-06-28
> **niteshifter said:**
> Hi,

/usr/share/scribus/templates

Thank You !
I Found It :)

---

### Post by drdave69 on 2009-06-28
Ok new problem...same topic.
When I try to extract the template into the folder, I get this error message 
"Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///usr/share/scribus/templates"
"
I installed Scribus from the repository, I have heard that when things are installed from there, the user (me) does not have admin rights.
How do I change the permissions of this program (or any program), so I can install templates?

---

### Post by oldos2er on 2009-06-28
Use "sudo" to give yourself admin privileges; e.g. **sudo tar zxvf somefile.tar.gz /usr/share/scribus/templates**

---

### Post by drdave69 on 2009-06-29
> **oldos2er said:**
> Use "sudo" to give yourself admin privileges; e.g. **sudo tar zxvf somefile.tar.gz /usr/share/scribus/templates**

Ok I tried the line 

**sudo tar zxvf garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates**

and it did not work.

I get this error:

tar: garage-sale-bw-a4.sla_.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /usr/share/scribus/templates: Not found in archive
tar: Error exit delayed from previous errors

The file "garage-sale-bw-a4.sla_.gz" is located on my desktop.
Any suggestions?

---

### Post by decoherence on 2009-06-29
> **drdave69 said:**
> Ok I tried the line 

**sudo tar zxvf garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates**

and it did not work.

I get this error:

tar: garage-sale-bw-a4.sla_.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /usr/share/scribus/templates: Not found in archive
tar: Error exit delayed from previous errors

The file "garage-sale-bw-a4.sla_.gz" is located on my desktop.
Any suggestions?


sudo tar zxvf Desktop/garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates

---

### Post by drdave69 on 2009-06-29
> **decoherence said:**
> sudo tar zxvf Desktop/garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates

Tried this and now I get this error:

tar: This does not look like a tar archive
tar: Skipping to next header
tar: /usr/share/scribus/templates: Not found in archive
tar: Error exit delayed from previous errors

Any help would be greatly appreciated.
Thanks

---

### Post by decoherence on 2009-06-29
oops.... I shoulda read better. Try this.

sudo gunzip Desktop/garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates

---

### Post by drdave69 on 2009-06-29
> **decoherence said:**
> oops.... I shoulda read better. Try this.

sudo gunzip Desktop/garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates

Tried this and got this error:

gzip: /usr/share/scribus/templates is a directory -- ignored

---

### Post by drdave69 on 2009-06-29
We seem to be getting closer :)

---

### Post by drdave69 on 2009-06-29
Does anyone know what this means?


gzip: /usr/share/scribus/templates is a directory -- ignored

---

### Post by oldos2er on 2009-06-29
Try [B]sudo gunzip ~/Desktop/garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates/

[/B]

---

### Post by drdave69 on 2009-06-29
> **oldos2er said:**
> Try [B]sudo gunzip ~/Desktop/garage-sale-bw-a4.sla_.gz /usr/share/scribus/templates/

[/B]

tried this now I get this error:

gzip: /home/david/Desktop/garage-sale-bw-a4.sla_.gz: No such file or directory
gzip: /usr/share/scribus/templates/ is a directory -- ignored

BUT... now the file on my desktop is unzipped, it is now named:

garage-sale-bw-a4.sla_

and for some reason the .gz file is missing.

---

### Post by oldos2er on 2009-06-29
So you extracted the file to your desktop? Then you can copy the contents of that folder to /usr/share/scribus/templates (which requires admin privileges).

---

### Post by drdave69 on 2009-06-29
> **oldos2er said:**
> So you extracted the file to your desktop? Then you can copy the contents of that folder to /usr/share/scribus/templates (which requires admin privileges).

Yes, exactly :)
My question is, how do I get the file into the folder, I am unable to cut & paste it, and when I try to drag & drop it I get this error:

Error moving file: Permission denied

How do I get admin privileges on my own computer?
Seems to me I should already have them.
Once again, program was installed using Synaptic.

Any Ideas, help, or insight would be GREATLY APPRECIATED
Thanks

---

### Post by Celauran on 2009-06-29
Open a terminal and type:

```
sudo mv Desktop/garage-sale-bw-a4.sla_ /usr/share/scribus/templates
```

---

### Post by drdave69 on 2009-06-29
> **Celauran said:**
> Open a terminal and type:

```
sudo mv Desktop/garage-sale-bw-a4.sla_ /usr/share/scribus/templates
```

Thank you :)
it is now there.

---

### Post by decoherence on 2009-06-29
Way back in 2007 there was talk about getting Nautilus and PolicyKit working in such a way that, rather than getting unhelpful permissions denied errors, you would be asked to authenticate.

I don't know what the status of that is now but it would make things like this MUCH easier. Half of the problems we had in this thread were due to people (including myself) posting wrong or mis-remembered commands.

---

### Post by Azrael3000 on 2009-06-29
I think that would be a very nice idea

---

### Post by oldos2er on 2009-06-29
You can run Nautilus with admin privileges using **gksu nautilus**

---

### Post by decoherence on 2009-06-30
Here is the GNOME bug report regarding this feature.

[http://bugzilla.gnome.org/show_bug.cgi?id=490200](http://bugzilla.gnome.org/show_bug.cgi?id=490200)

Running nautilus as admin works too, but this would be nicer. Anyway, I gone OT. Bad me!

---

