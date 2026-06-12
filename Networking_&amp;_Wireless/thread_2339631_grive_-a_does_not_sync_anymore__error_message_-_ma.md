---
title: "grive -a does not sync anymore  error message - malloc(): memory corruption"
date: 2016-10-11
forum: Networking &amp; Wireless
---

### Post by chandrakala2 on 2016-10-11
I had installed grive on ubuntu 16.04 TLS. It worked well the first few instances of syncing with  "grive  —a" command. However recently it does not seem to sync anything.

The command    ```
grive —dry-run
```
outputs a long error message a part of it is pasted below. 
```
 adminuser-desktop:~/grive> grive —dry-runReading local directories
Reading remote server file list
*** Error in `grive': malloc(): memory corruption: 0x0000000003545000 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x77725)[0x7f446572a725]
/lib/x86_64-linux-gnu/libc.so.6(+0x819be)[0x7f44657349be]
/lib/x86_64-linux-gnu/libc.so.6(__libc_malloc+0x54)[0x7f44657365a4]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_Znwm+0x18)[0x7f4465d1fe78]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZNSs4_Rep9_S_createEmmRKSaIcE+0x59)[0x7f4465d60e39]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0xcef47)[0x7f4465d60f47]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZNSsC2EPKcRKSaIcE+0x36)[0x7f4465d62d16]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZNSt11logic_errorC2EPKc+0x36)[0x7f4465d45b06]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZNSt12length_errorC2EPKc+0x9)[0x7f4465d45b89]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZSt20__throw_length_errorPKc+0x29)[0x7f4465d48259]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x11f099)[0x7f4465db1099]
grive(_ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEE12_M_constructIPcEEvT_S7_St20forward_iterator_tag+0x91)[0x5479b5]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1ERKS4_+0x1f)[0x7f4465db39cf]
grive(_ZNK2gr8Resource3MD5B5cxx11Ev+0x27)[0x5362e1]
grive(_ZNK5boost11multi_index13const_mem_funIN2gr8ResourceENSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEEXadL_ZNKS3_3MD5B5cxx11EvEEEclERKS3_+0x36)[0x52abbe]
grive(_ZNK5boost11multi_index13const_mem_funIN2gr8ResourceENSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEEXadL_ZNKS3_3MD5B5cxx11EvEEEclIPS3_EENS_10disable_ifINS_14is_convertibleIRKT_RKS3_EES9_E4typeESH_+0x3d)[0x529627]
grive(_ZN5boost11multi_index6detail12hashed_indexINS0_13const_mem_funIN2gr8ResourceENSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEEXadL_ZNKS5_3MD5B5cxx11EvEEEENS_4hashISB_EESt8equal_toISB_ENS1_9nth_layerILi2EPS5_NS0_10indexed_byINS0_17hashed_non_uniqueINS0_3tagINS4_7details6ByHrefEN4mpl_2naESP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_EENS3_IS5_SB_XadL_ZNKS5_8SelfHrefB5cxx11EvEEEESP_SP_EENSK_INSL_INSM_5ByMD5ESP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_EESC_SP_SP_EENS0_13hashed_uniqueINSL_INSM_10ByIdentityESP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_EENS0_8identityISI_EESP_SP_EESP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_SP_EESaISI_EEENS_3mpl6v_itemIST_NS15_7vector0ISP_EELi0EEENS1_21hashed_non_unique_tagEE16unchecked_rehashEmS1A_+0x1e1)[0x52e8e3]
.
.
```
.....it goes on for a many more lines like above and ends with the following line
```
.
7ffd96fe9000-7ffd96feb000 r--p 00000000 00:00 0                          [vvar]
7ffd96feb000-7ffd96fed000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Abort (core dumped)

```
If possible please let me know how to sort this out.

---

### Post by ajgreeny on 2016-10-11
I'm afraid I can not help with your problem, but when posting in future please use **Code-Tags** for terminal output.

See my signature below for a **How-to**

---

