---
title: "draw using C programming in Linux"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by green_gal on 2007-08-16
how do i draw using C programming in Linux? there is quite a few websites that provide the answers but wenever i run it in linux terminal these error comes up: 

draw1.c:2:22: error: plot_xps.h: No such file or directory

**this is the code:**

#include <stdio.h>
#include <plot_xps.h>
main()
{
	int j;
	ps_iniplot(0, "cercle.ps", 0,0,0.,0.,1.,"");
	ps_origin(7.,5.,0.,0.);				/* go 7cm right and 5cm up*/
								/*circles drawing */
	ps_disk(.25,0.);					/*draws a disk */
	for(j = 0; j< 4; j++)
	{
		ps_circle((float)j);			/* draws 4 circles*/
		ps_movea(0.,2.);				/*go 2cm up*/
	}
	/*drawing of ellipses*/
	ps_ellip_disk(.5,.25,.6);			/*draws a grey ellipse*/
	for(j = 0; j< 4; j++)				/*and 4 ellipses*/
	{
		ps_ellipse((float)j, (float)j/2.);
	}
	ps_endplot('f');				/*keep the file*/
} /*main*/

i think the problem is that i don't have the plot_xps.h library. can anybody tell me how to download? thanks.

---

### Post by nicolas2b on 2007-08-16
A better solution : use cairo (cairographics.org)

---

### Post by bashologist on 2007-08-16
```
satan@ubuntu:~$ aptitude search plot
...
p   xplot                           - A simple x-y column data plotter for X.
```
Maybe this?

---

