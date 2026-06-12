---
title: "Why am I get ths i the gprof flat profile."
date: 2010-11-15
forum: New to Ubuntu
---

### Post by newport_j on 2010-11-15
```

 
Flat profile:
Each sample counts as 0.01 seconds.
% cumulative self self total 
time seconds seconds calls s/call s/call name 
29.53 1.37 1.37 716248 0.00 0.00 RAY_SGM2
29.09 2.72 1.35 127638 0.00 0.00 INT_BND2
8.19 3.10 0.38 76518 0.00 0.00 PRC_RAY2
8.19 3.48 0.38 CHN_RFL2
4.53 3.69 0.21 WEGprint
3.02 3.83 0.14 500 0.00 0.00 RAY_TYP2
3.02 3.97 0.14 GNR_SEQ
2.16 4.07 0.10 5 0.02 0.02 VLM_ATN3
1.72 4.15 0.08 127638 0.00 0.00 NRM_BND2
1.72 4.23 0.08 1 0.08 3.10 PRC_BRN2
1.51 4.30 0.07 693307 0.00 0.00 TRA_RAY2
1.51 4.37 0.07 76518 0.00 0.00 VRT_SRF2
1.29 4.43 0.06 1627607 0.00 0.00 LWR_VTX2
0.86 4.47 0.04 1500 0.00 0.00 VRT_TIM2
0.65 4.50 0.03 57376 0.00 0.00 STR_EIG
0.43 4.52 0.02 125340 0.00 0.00 SBL94
0.43 4.54 0.02 76518 0.00 0.00 VRT_BTM2
0.43 4.56 0.02 70973 0.00 0.00 gsiz2des
 
 

```
 
 
What does this flat profile mean for CHN_RFL2.C, WEGprint, GNR_SEQ, and DCM_SGM2.C?
 
They have no info for columns for calls, 
self, total
s/call s/call
 
 
All the oher functions have information for these columns - but not the functions I just listed.
 
 
Newport_j

---

### Post by talonmies on 2010-11-16
It means those functions were not profiled, most likely because they were not compiled for profiling.

---

### Post by newport_j on 2010-11-16
That seems like a good answer except that they were compiled for profiling. There must be another reason.
 
 
Newport_j

---

### Post by talonmies on 2010-11-16
To quote the gnu gprof documentation:

> 
This is the total number of times the function was called. If the function was never called, or the number of times it was called cannot be determined (probably because the function was not compiled with profiling enabled), the calls field is blank.Given you don't use make, I am 99% certain you left off the profiler flag to the compilation statement for the file or files containing those functions.

---

### Post by newport_j on 2010-11-17
I recompiled the program using the file now shown:
 
 
[code]
#!/bin/sh
gcc -m32 -lm -lrt -pg -O0 -o grab WEGtest.c InitializeScenarioData.c WAFmutex.c P_tra_ray2.c thread.c P_prc_typ2.c set_nod2.c env_nodb.c vlm_atnb.c tra_ray2.c zro_rng2.c lin_lin.c test_vlm_atn3.c prc_typ2.c ray_sgm2.c vlm_atn3.c ray_typ2.c test_ndx_tbl.c str_eig.c zsbl94.c snd_slw2.c ndx_tbl.c btm_dptb.c lwr_vtx2.c rfl_srf2.c rfl_btm2.c zbtms94.c zbtmrf9.c vrt_typ2.c dcm_sgm2.c vrt_tim2.c prc_ray2.c vrt_srf2.c srf_int2.c vrt_btm2.c btm_int2.c vrt_ray2.c gnr_seq.c chn_rfl2.c unfold2.c int_bnd2.c nrm_bnd2.c zblos94.c zbtmr04.c zsigmpr.c zsigmpv.c trn_mtx2.c adv_mtx2.c zelblos.c zbrlael.c WAFmathComplex.c fmod.c zgsiz2des.c zgam.c zbeta.c WEG.c src_ang2.c prc_brn2.c merge.c IntSrcRays.c
[code/] 
 
I am unable to show the flat prfile. I do not know how to post graphics on a Forum thread/message. I know how to post code, but not a png file. I cannot post it. If I knew how I would post it. 
 
 
It essentially says the same thing as before. The chn_rfl2 file has no info on two of its columns. This is also true of WEGprint.c and GNR_SEQ. I am not sure why. As you can see from the compile command the files in quesation were compiled for profiling just as all the other files were compiled for profiling.
 
Why am I getting only half info on CHN_RFL2, WEGprnt and GNR_SEQ? 
 
 
Newport_j

---

### Post by newport_j on 2010-11-18
I have attach a pmg file of the output of my flat profile. I am not sure why chn_rfl2 and gnr_seq had no info in the calls, self s/call and total s/call columns.
 
The immediate and previous post talk about this message also.
 
Newport_j

---

