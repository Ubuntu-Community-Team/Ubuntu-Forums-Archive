---
title: "R commander disappears"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by matyasfalvi on 2009-03-04
Hi All!

I haven't used R commander in a while. Today I wanted to use it again. 

However when I type:

```
library(Rcmdr)
```
it says:
```
Error in library(Rcmdr) : there is no package called 'Rcmdr'

```
Does anyone have a clue as to what is or was going on here?

Thanx a bunch in advance!

---

### Post by kanikilu on 2009-03-04
Are you sure that package is installed? It's been a while since I've used R, but I think you can check by using:

```
installed.packages()
```

If all else fails, can you just re-install the package?

```
install.packages("Rcmdr", dependencies=TRUE)
```

---

### Post by matyasfalvi on 2009-03-07
Hi!

yes I looked at it that is what I get:

> 

> installed.packages()
           Package      LibPath              Version   Priority      Bundle
base       "base"       "/usr/lib/R/library" "2.8.1"   "base"        NA    
boot       "boot"       "/usr/lib/R/library" "1.2-35"  "recommended" NA    
class      "class"      "/usr/lib/R/library" "7.2-45"  "recommended" "VR"  
cluster    "cluster"    "/usr/lib/R/library" "1.11.12" "recommended" NA    
codetools  "codetools"  "/usr/lib/R/library" "0.2-1"   "recommended" NA    
datasets   "datasets"   "/usr/lib/R/library" "2.8.1"   "base"        NA    
foreign    "foreign"    "/usr/lib/R/library" "0.8-32"  "recommended" NA    
graphics   "graphics"   "/usr/lib/R/library" "2.8.1"   "base"        NA    
grDevices  "grDevices"  "/usr/lib/R/library" "2.8.1"   "base"        NA    
grid       "grid"       "/usr/lib/R/library" "2.8.1"   "base"        NA    
KernSmooth "KernSmooth" "/usr/lib/R/library" "2.22-22" "recommended" NA    
lattice    "lattice"    "/usr/lib/R/library" "0.17-20" "recommended" NA    
MASS       "MASS"       "/usr/lib/R/library" "7.2-45"  "recommended" "VR"  
methods    "methods"    "/usr/lib/R/library" "2.8.1"   "base"        NA    
mgcv       "mgcv"       "/usr/lib/R/library" "1.5-0"   "recommended" NA    
nlme       "nlme"       "/usr/lib/R/library" "3.1-90"  "recommended" NA    
nnet       "nnet"       "/usr/lib/R/library" "7.2-45"  "recommended" "VR"  
rpart      "rpart"      "/usr/lib/R/library" "3.1-42"  "recommended" NA    
spatial    "spatial"    "/usr/lib/R/library" "7.2-45"  "recommended" "VR"  
splines    "splines"    "/usr/lib/R/library" "2.8.1"   "base"        NA    
stats      "stats"      "/usr/lib/R/library" "2.8.1"   "base"        NA    
stats4     "stats4"     "/usr/lib/R/library" "2.8.1"   "base"        NA    
survival   "survival"   "/usr/lib/R/library" "2.34-1"  "recommended" NA    
tcltk      "tcltk"      "/usr/lib/R/library" "2.8.1"   "base"        NA    
tools      "tools"      "/usr/lib/R/library" "2.8.1"   "base"        NA    
utils      "utils"      "/usr/lib/R/library" "2.8.1"   "base"        NA    
           Contains                 
base       NA                       
boot       NA                       
class      "MASS class nnet spatial"
cluster    NA                       
codetools  NA                       
datasets   NA                       
foreign    NA                       
graphics   NA                       
grDevices  NA                       
grid       NA                       
KernSmooth NA                       
lattice    NA                       
MASS       "MASS class nnet spatial"
methods    NA                       
mgcv       NA                       
nlme       NA                       
nnet       "MASS class nnet spatial"
rpart      NA                       
spatial    "MASS class nnet spatial"
splines    NA                       
stats      NA                       
stats4     NA                       
survival   NA                       
tcltk      NA                       
tools      NA                       
utils      NA                       
           Depends                                          
base       NA                                               
boot       "R (>= 2.5.0), graphics, stats"                  
class      "R (>= 2.4.0), grDevices, graphics, stats, utils"
cluster    "R (>= 2.5.0), stats, graphics, utils"           
codetools  "R (>= 2.1)"                                     
datasets   NA                                               
foreign    "R (>= 2.6.0), stats"                            
graphics   NA                                               
grDevices  NA                                               
grid       NA                                               
KernSmooth "R (>= 2.5.0), stats"                            
lattice    "R (>= 2.5.0)"                                   
MASS       "R (>= 2.4.0), grDevices, graphics, stats, utils"
methods    NA                                               
mgcv       "R (>= 2.3.0)"                                   
nlme       "graphics, stats, R (>= 2.4.0)"                  
nnet       "R (>= 2.4.0), grDevices, graphics, stats, utils"
rpart      "R (>= 2.7.0), graphics, stats, grDevices"       
spatial    "R (>= 2.4.0), grDevices, graphics, stats, utils"
splines    NA                                               
stats      NA                                               
stats4     "methods, graphics, stats"                       
survival   "stats, utils, graphics, splines, R (>= 2.6.0)"  
tcltk      NA                                               
tools      NA                                               
utils      NA                                               
           Imports                                  
base       NA                                       
boot       NA                                       
class      NA                                       
cluster    NA                                       
codetools  NA                                       
datasets   NA                                       
foreign    "methods, utils"                         
graphics   "grDevices"                              
grDevices  NA                                       
grid       "grDevices"                              
KernSmooth NA                                       
lattice    "grid, grDevices, graphics, stats, utils"
MASS       NA                                       
methods    "utils"                                  
mgcv       "graphics, stats"                        
nlme       "lattice"                                
nnet       NA                                       
rpart      NA                                       
spatial    NA                                       
splines    "graphics, stats"                        
stats      NA                                       
stats4     NA                                       
survival   NA                                       
tcltk      NA                                       
tools      NA                                       
utils      NA                                       
           Suggests                    OS_type Built  
base       NA                          NA      "2.8.1"
boot       "survival"                  NA      "2.8.1"
class      "lattice, nlme, survival"   NA      "2.8.0"
cluster    NA                          NA      "2.8.1"
codetools  NA                          NA      "2.7.1"
datasets   NA                          NA      "2.8.1"
foreign    NA                          NA      "2.8.1"
graphics   NA                          NA      "2.8.1"
grDevices  NA                          NA      "2.8.1"
grid       "lattice"                   NA      "2.8.1"
KernSmooth "MASS"                      NA      "2.7.2"
lattice    "grid"                      NA      "2.8.1"
MASS       "lattice, nlme, survival"   NA      "2.8.0"
methods    NA                          NA      "2.8.1"
mgcv       "nlme (>= 3.1-64), splines" NA      "2.8.1"
nlme       NA                          NA      "2.8.1"
nnet       "lattice, nlme, survival"   NA      "2.8.0"
rpart      "survival"                  NA      "2.8.0"
spatial    "lattice, nlme, survival"   NA      "2.8.0"
splines    NA                          NA      "2.8.1"
stats      NA                          NA      "2.8.1"
stats4     NA                          NA      "2.8.1"
survival   NA                          NA      "2.7.0"
tcltk      NA                          NA      "2.8.1"
tools      NA                          NA      "2.8.1"
utils      NA                          NA      "2.8.1"
> rpart
Error: object "rpart" not found
> library(rpart)
> install.packages=("Rcmdr", dependencies=True)
Error: unexpected ',' in "install.packages=("Rcmdr","
> install.packages=(Rcmdr, dependencies=True)
Error: unexpected ',' in "install.packages=(Rcmdr,"
> install.packages("Rcmdr", dependencies=TRUE)
Warning in install.packages("Rcmdr", dependencies = TRUE) :
  argument 'lib' is missing: using '/usr/local/lib/R/site-library'
Warning in install.packages("Rcmdr", dependencies = TRUE) :
  'lib = "/usr/local/lib/R/site-library"' is not writable
Would you like to create a personal library
'~/R/i486-pc-linux-gnu-library/2.8'
to install packages into?  (y/n) 




---

### Post by matyasfalvi on 2009-03-11
Hi!

I reinstalled it, and now it is working fine! Thanx for the help!

---

### Post by matyasfalvi on 2009-04-22
Hi All!

Well it just disappeared again I really don't know why this is happening but it is a bit annoying I can say that for sure. 

Could it be that it has to do something with the updates may be the updates somehow reset the configuration to default???

Any help is much appreciated!

Thanx a lot!

---

