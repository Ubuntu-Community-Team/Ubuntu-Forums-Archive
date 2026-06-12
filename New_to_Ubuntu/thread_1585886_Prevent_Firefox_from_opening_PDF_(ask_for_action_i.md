---
title: "Prevent Firefox from opening PDF (ask for action instead)"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-10-01
Until yesterday, when I clicked on a PDF, Firefox would ask me what I wanted to do: Save the file or open with Adobe.

That was exactly as I wanted.

Yesterday, I installed [PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636/"), but it didn't work, so I uninstalled it again.

Since then, when I click on a PDF, Firefox opens the PDF inside itself. It doesn't give me the option to save or open in Adobe.

My preferences show that PDF is set to "Always ask" (see screenshot). When I look at my add-ons (Tools > Add-ons), I see none that refers to Adobe or PDF.

How do I revert Firefox to giving the pop-up dialogue for PDFs?

---

### Post by Phil D. on 2010-10-01
Not sure if this is the solution - but have a look in the properties of a pdf file (in nautilus - right click) and check the default action.

---

### Post by Paddy Landau on 2010-10-01
Thanks for the idea, but Adobe already is default.

---

### Post by Paddy Landau on 2010-10-01
Huh! I just found the answer, and it's not at all intuitive!


[LIST=1]
[*]Go to the preferences and change "Always ask" to "Use Adobe Reader 9 (default)".
[*]Click on a PDF link (Adobe opens). Close Adobe.
[*]Go back to the preferences and change it back to "Always ask".
[*]Now it asks.
[/LIST]

:confused:

---

### Post by lovinglinux on 2010-10-01
> **Paddy Landau said:**
> Huh! I just found the answer, and it's not at all intuitive!


[LIST=1]
[*]Go to the preferences and change "Always ask" to "Use Adobe Reader 9 (default)".
[*]Click on a PDF link (Adobe opens). Close Adobe.
[*]Go back to the preferences and change it back to "Always ask".
[*]Now it asks.
[/LIST]

:confused:

Must be a bug. You should report it.

[https://bugzilla.mozilla.org/enter_bug.cgi](https://bugzilla.mozilla.org/enter_bug.cgi)

---

### Post by Paddy Landau on 2010-10-01
> **lovinglinux said:**
> Must be a bug. You should report it.
I suspect it was a bug with the PDF Download add-on. It didn't work, so I uninstalled it, and I think it left some setting that it had adjusted.

---

