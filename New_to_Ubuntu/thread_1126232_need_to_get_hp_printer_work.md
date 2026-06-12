---
title: "need to get hp printer work"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Ubunser on 2009-04-15
Hello! I have Ubuntu 8.10. and problems with printing. Printer - HP Deskjet D1360. It worked under Windows, but now I have only Ubuntu.
When I press 'print' it simulates printing, but the sheet comes out blank. Sometimes it ignores printing commands and builds up a queue. 
Often a message pops up 'a printer may not be connected'

or 'there is an error'

I tried disconnecting it, restarting and reconnecting, but no way.
So, it does print, but the sheet comes out blank. I don't think those are cartridges, they have been working for two years. It's Ubuntu, I think. I am not very deep in Ubuntu especially, so plain language would save time. Thank you

---

### Post by halitech on 2009-04-15
according to OpenPrinting.org the machine should mostly work.

[http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1360](http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_D1360)

Did you install hpijs?

---

### Post by khelben1979 on 2009-04-15
Check out HPLIP. You'll find it [here]("http://hplipopensource.com/hplip-web/index.html").

---

### Post by Ubunser on 2009-04-15
> **halitech said:**
> 
Did you install hpijs?

Sorry, what is it and how can I check it.

---

### Post by Ubunser on 2009-04-15
> **khelben1979 said:**
> Check out HPLIP. You'll find it [here]("http://hplipopensource.com/hplip-web/index.html").

Is there a chance I have it installed? Or should I click download?

---

### Post by halitech on 2009-04-15
open synaptic and check if it is listed and installed, if its not installed but listed, install it then readd your printer. If not, go with the download that khelben suggested.

---

### Post by Ubunser on 2009-04-15
Yes, I have hpijs 2.8.7-Ubuntu6 marked with green box in synaptic. Also I started downloading hplip, but not finished. Abort it?

---

### Post by halitech on 2009-04-15
that should have it working. how long has it been since you last used the printer?

---

### Post by Ubunser on 2009-04-15
I probably had it from the beginning with distribution. I used printer half an hour ago

---

### Post by Ubunser on 2009-04-15
Here what I see in File - print

---

### Post by halitech on 2009-04-15
looks like you have 3 printers installed, try removing them all, unplugging the printer, wait a minute then plug it back in and see what happens

---

### Post by Ubunser on 2009-04-15
also I saw hplip in synuptic, just earlier version from what khelben1979 gave a link

---

### Post by halitech on 2009-04-15
was hplip also installed?

---

### Post by Ubunser on 2009-04-15
How do I delete a printer? I never did it before in Ubuntu. Don't know where to go or is this a terminal command?

---

### Post by Ubunser on 2009-04-15
> **halitech said:**
> was hplip also installed?

here

---

### Post by halitech on 2009-04-15
ok, both are installed

I think you just go into the Printing and right click and delete or remove

---

### Post by Ubunser on 2009-04-15
the right mouse button in File - print cannot be used unfortunately

---

### Post by halitech on 2009-04-15
file - remove then?

sorry, never had to remove a printer. Maybe you need to use CUPS to remove it

---

### Post by Sef on 2009-04-15
>  		How do I delete a printer? I never did it before in Ubuntu. Don't know where to go or is this a terminal command? 	

System > Administration > Printing

You should see the printers there.  Hightlight the printer to be deleted, then printer > delete.

I would delete all of them, then reinstall the printer.   Server > New > printer or turn the printer off about 30 seconds, then turn it on.  It should be automatically detected.

---

### Post by halitech on 2009-04-15
thanks Sef, I'm using XFCE so the options are a little different for me then what most see in Gnome.

---

### Post by Ubunser on 2009-04-17
Hi, guys! It is solved. I can't believe it. The problem was simple and hard to find as for a newbie. I was lucky to play with tabs in the right place, otherwise I would go round in circles having no idea what's wrong.

As I had 3 printers I deleted them, disconnected printer cable, restarted, connected it, and it was installed automatically.

So, I openned a file I wanted to print, then File - Print, in the openning window I highlighted the line with my printer. After this I can see the "Advanced" tab, in this tab under the word "General" I changed the "Printout Mode" from "Normal(Color Cartridge)" to "High Quality Grayscale(Black cartridge)". 
But I have to change this setting every time I have to print, as it is a default position. How to make Black Cartridge a default one.

But overall this is solved. Thank you very much. Ukraine loves you, God bless you!

Separate thanks for Halitech, you are helpful!

---

### Post by halitech on 2009-04-17
glad to hear you got it working :) 

no need to thank me, I just enjoy giving back to the community that helped me get started using Linux :)

---

