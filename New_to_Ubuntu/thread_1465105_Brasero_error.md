---
title: "Brasero error"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Paul T. on 2010-04-29
Whilst trying to burn 10.04 ISO image to disc, I received the following error:

BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 15
	message	= "An error occurred while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2808)

This occured right at the end when finalising disc, anyone know what it means?



*update*
Despite error disc seems to work ok, am writing this whilst running 10.04 off the live disc, strange.

---

### Post by satish_j on 2010-04-29
I used to get so many diff errors using	Brasero..
switched to K3B and not a single error now...
Try K3B for disc burning...

---

### Post by PriceChild on 2010-04-29
> **Paul T. said:**
> *update*
Despite error disc seems to work ok, am writing this whilst running 10.04 off the live disc, strange.
I would suggest running the disc integrity check, or verifying the md5sum of the disc to ensure it is all there. If you install from it and it isn't perfect, anything might happen.

Random other suggestion, I'd also suggest burning at a lower speed to try and see if that works.

---

### Post by Paul T. on 2010-04-29
Thx for the ideas, will try K3B as I've had other probs with Brasero before.

---

### Post by barbz127 on 2010-04-29
Only problem with k3b is all the kde dependencies it installs at the same time.

Brasero works fine for me.

---

### Post by Miljet on 2010-04-29
> Only problem with k3b is all the kde dependencies it installs at the same time.

My sentiments exactly. If I wanted all the kde dependencies, I would install Kubuntu in the first place. There has to be a Gnome based burning program that works.

---

### Post by SagnaB on 2010-07-27
> **Miljet said:**
> My sentiments exactly. If I wanted all the kde dependencies, I would install Kubuntu in the first place. There has to be a Gnome based burning program that works.
I second that. Surely there has to be!

---

