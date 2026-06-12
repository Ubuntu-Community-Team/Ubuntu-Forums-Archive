---
title: "Solution for 9.10 problems with Intel Grahic Chipset"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by spirou38 on 2010-01-18
I had a problem with an ASROCK G41M-GS board with an onboard Intel Graphic chipset : when trying to install Ubuntu 9.10, I always got a black screen.
 
For that board, [COLOR=green]**I found a solution in the BIOS **[/COLOR]:D :D :D :
 
I modified in "[COLOR=blue]Advanced[/COLOR]" > "[COLOR=blue]Chipset config[/COLOR]" :
1/ "[COLOR=blue]Primary graphic adaptor[/COLOR]" : replace the "[COLOR=blue]PCI[/COLOR]" default value by "[COLOR=blue]Onboard[/COLOR]" ;
2/ "[COLOR=blue]Share memory[/COLOR]" : replace the "[COLOR=blue]Auto[/COLOR]" default value by "[COLOR=blue]64MB[/COLOR]".
 
Perhaps there is no need of the 2 mods or perhaps another value than "64MB" will work, I had no time to make other tests.
 
With those BIOS changes, my mainboard can now boot in graphic mode.
 
I hope it will be available for other mother boards ;).

---

