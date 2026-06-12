---
title: "Swiftfox questions - faster firefox"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-03
Have some questions about the Swiftfox optimised build:

1.Why is swiftfox faster than Firefox? What exactly do they do?

2.Does it install as a separate app, if so, where is it located? More importantly, which profiles does it use (same as firefox?) and if it uses own profiles, where are they located?

3.I have a minor installation problem. I installed it from the official .deb file

It does not show up by quick searching in the default synaptic view which is sections>ALL in the left pane. but then if I go and change the classification to status and category to installed (local and obsolete), it shows swiftfox-prescott along with all the other apps I have installed using .debs.

More weird is the fact that quicksearching using the snaptic search bar brings up nothing, not even when I have the status>installed pane open (which has only 9 apps/listings). BUT if instead of using the search bar, I manually click on the search icon (the binoculars) and then attempt to search, it finds it successfully.

Whats going on?

Thanks a lot

---

### Post by shae on 2009-07-03
The primary focus of newer builds of swiftfox is that they use PGO, a method that better optimizes the final build at the cost of taking longer to compile (it compiles twice).

I believe the firefox from the repository does not use PGO.  Furthermore, Swiftfox changes a few settings within Firefox that can add aditional speed.

I am using Firefox 3.5 + PGO on ArchLinux and it works quite well.

---

### Post by lovinglinux on 2009-07-03
> **Andy06 said:**
> 1.Why is swiftfox faster than Firefox? What exactly do they do?

Swiftfox is compiled using optimizations for specific processors. So it "talks" better with your CPU, increasing it's performance. That's why your swiftfox package is named swiftfox-prescott. Prescott is the code name of a generation of Intel Pentium 4 processors.

You can also do that if you are whiling to compile yourself. Is not that complicated. I just compiled Firefox 3.5 and it gets a 30% performance boost on my machine. If you are interested, I have written a simple tutorial on how to compile Firefox and also several tips on how to optimize it. Check it out at [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

> **Andy06 said:**
> 2.Does it install as a separate app, if so, where is it located? More importantly, which profiles does it use (same as firefox?) and if it uses own profiles, where are they located?

Yes, it does install a separate app. I don't remember exactly, but I guess it is in the /opt/ directory or under /usr/local/lib. Nevertheless, it uses the same profiles as Firefox.

---

### Post by Andy06 on 2009-07-03
I remember reading from someone from the Mozilla team somewhere that FFv3.0 did not use PGO on Linux but did so in Windows. 

1.So in theory, Swiftfox would have no improvement in performance over FF in windows?

2.Does FFv3.5 use PGO in linux?

3.I have a Core 2 duo 1.83 GHz, should I be something apart from prescott ideally?

4.How do I run the swiftfox profile manager, then I can make a separate profile for it that does not mess with my regular FF profile.

5.Why won't it show up in synaptic (see original post).

Thanks a lot :D

---

### Post by Andy06 on 2009-07-03
It is not in /opt/ directory or under /usr/local/lib.

Where do manually installed .deb files usually go? Where do synaptic, add/remove and apt get installed files usually go? I will try searching those locations as well.

Thanks a lot once again.

---

### Post by lovinglinux on 2009-07-03
> **Andy06 said:**
> I remember reading from someone from the Mozilla team somewhere that FFv3.0 did not use PGO on Linux but did so in Windows. 

That's true.

> **Andy06 said:**
> 1.So in theory, Swiftfox would have no improvement in performance over FF in windows?

The official Firefox can't be optimized for all processors at the same time, so compiling your self with processor specific optimizations or using Swiftfox tailored for your CPU family will increase performance, no matter if you have PGO enabled or not. [PGO](https://developer.mozilla.org/en/Building_with_Profile-Guided_Optimization) is another type of optimization that compiles in two passes, like for example when you convert a video in two passes.

> **Andy06 said:**
> 2.Does FFv3.5 use PGO in linux?

Yes. I think so.

> **Andy06 said:**
> 3.I have a Core 2 duo 1.83 GHz, should I be something apart from prescott ideally?

Yes. Try to find yours on these links:

[http://en.wikipedia.org/wiki/Comparison_of_Intel_processors](http://en.wikipedia.org/wiki/Comparison_of_Intel_processors)
[http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2)

> **Andy06 said:**
> 4.How do I run the swiftfox profile manager, then I can make a separate profile for it that does not mess with my regular FF profile.

Since they share profiles, you can do that from firefox

Run this command:

```
firefox -P
```

> **Andy06 said:**
> 5.Why won't it show up in synaptic (see original post).

Don't know.

---

### Post by Andy06 on 2009-07-03
Ok I din't understand any of the technical stuff :D 
I will read some more on the links you gave and try to understand it.

So Swiftfox does not have its own profile manager? So I'll create a swiftfox profile from the firefox profile manager and then add a switch to the launcher which executes its relevant profile directly? That should work, shouldn't it?

So basically with v3.5 swiftfox and FF both have PGO but only Swiftfox is also optimised for your CPU?

With FFv3.5 using PGO in linux, how much of a performance difference do you "feel"? I feel none. 

Thanks a lot for your help :D

---

### Post by Paul T. on 2009-07-03
I've just installed Swiftfox and am having problems.

When I open Swiftfox I get 2 tabs, one my home page and the other "404: file not found  Mozilla.Org"

If I open Firefox I now get pop up window checking on installed applets

My Evolution email accounts have gone, now I get the "Welcome to Evolution" set up window.

Tried to remove Swiftfox but it's not listed in either add/remove or Synaptic. 
Not pleased :-x

---

### Post by Andy06 on 2009-07-03
I'll help with what I can.

> When I open Swiftfox I get 2 tabs, one my home page and the other "404: file not found Mozilla.Org"

The "404: file not found Mozilla.Org" is fine, its linking to an expired page and that is no major concern.

> If I open Firefox I now get pop up window checking on installed applets

That is fine too. What happens is, instead of creating a profile for itself, swiftfox accesses  your firefox profile (data, bookmarks, history, passwords), the exact same one, not a copy. So the firefox code inside swiftfox thinks you've changed versions, so it runs that check when you run Swiftfox. Then when you run Firefox again, it again detects another version from the previous run (which was swiftfox), so it runs this check again. No problem here.

> My Evolution email accounts have gone, now I get the "Welcome to Evolution" set up window.

No clue. This might be unrelated btw. What version of Firefox are you using? Perhaps you are getting the random right click bug. Let me know if you are using a version below v3.0.10. Most likely this is unrelated though. Perhaps you changed something else on your system around the same time?

> Tried to remove Swiftfox but it's not listed in either add/remove or Synaptic.

Yeah I don't know why it is not listed but usually if you give it 4-5 reboots, it eventually will be. Totally nonsensical behaviour I know.
If you want to find it immediately. There is a way.

If you installed by unzipping a tar.gz, then it has no files elsewhere and you can delete the whole folder and everything will go. If you ran a script to install from tar.gz, then I have no clue

If you installed using a .deb file. Then it is infact there in Synaptic, Synaptic is just too stupid to find it and will need some help :)
In the left pane of synaptic, you will see Sections>All is highlighted.
Change Sections to Status classification and then try the ALL, Installed and Installed (local or obselete categories), you will see it there.

Alternatively, you can click on the binocular icon after opening synaptic and run a full search instead of a quick search, that finds it too. Simply enter "swiftfox" and nothing else. I don't know why this search is different from the quick search right next to it and why they produce different results, but again thats how it is.

If you din't like this experience, try downloading the swiftfox tar.gz and simply unzip it, it works completely from a single folder. I wish all apps on linux were just tar.gz self contained ones hehe.

---

### Post by l-x-l on 2009-07-03
I tried swiftfox-athelon64 a few weeks ago & it did seem speedy but none of my plugin worked. NONE. Extensions worked as did everything else except plugins. So I couldn't view youtube or flash content, no go for java either. 

I tried searching for help via google & forums but got no answers. So back to FF & Opera.

---

### Post by Andy06 on 2009-07-03
Find out where it is installed and manually copy the plugins over. That works on windows. I hope it works for you

---

### Post by l-x-l on 2009-07-03
> **Andy06 said:**
> Find out where it is installed and manually copy the plugins over. That works on windows. I hope it works for you

The FF plugins are installed in ~/.mozilla/plugins. I already tried copying them to /usr/lib/swiftfox/plugins as well as /usr/lib64/swiftfox/plugins. Neither of which worked for me. I posted a msg in the swiftfox forums & have never gotten a response. If you can think of any other location I could try, please let me know.

---

### Post by Andy06 on 2009-07-04
Are they loading though? 

Start Swiftfox and check if they are loading as disabled or not loading (not detected) at all.

---

### Post by l-x-l on 2009-07-04
> **Andy06 said:**
> Are they loading though? 

Start Swiftfox and check if they are loading as disabled or not loading (not detected) at all.

They are not detected at all.

---

### Post by lovinglinux on 2009-07-04
> **Andy06 said:**
> So Swiftfox does not have its own profile manager? So I'll create a swiftfox profile from the firefox profile manager and then add a switch to the launcher which executes its relevant profile directly? That should work, shouldn't it.

Try 

```
swiftfox -P
```

and

```
swiftfox profilename
```


It should work. Neverthless, since they share profiles, it doesn't matter if you create the profile with Firefox or Siftfox. Both will detect it.

> **Andy06 said:**
> So basically with v3.5 swiftfox and FF both have PGO but only Swiftfox is also optimised for your CPU?

Yes.

> **Andy06 said:**
> With FFv3.5 using PGO in linux, how much of a performance difference do you "feel"? I feel none.

I haven't tried yet. PGO is not something that you turn on an off. It's a thing that you enable during the compilation of the program. I will compile it with PGO and see if there is any difference. Will post my results tomorrow.

---

### Post by shae on 2009-07-05
Firefox 3.5 without PGO(official from site): [http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B63,62,62,63,62%5D,%223d-morph%22:%5B46,40,41,41,47%5D,%223d-raytrace%22:%5B102,102,99,99,100%5D,%22access-binary-trees%22:%5B53,52,53,54,53%5D,%22access-fannkuch%22:%5B77,77,77,77,85%5D,%22access-nbody%22:%5B36,35,34,34,36%5D,%22access-nsieve%22:%5B15,15,14,15,16%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,2,1%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,2,3,3,2%5D,%22bitops-nsieve-bits%22:%5B37,37,35,35,35%5D,%22controlflow-recursive%22:%5B45,43,44,44,43%5D,%22crypto-aes%22:%5B47,44,47,43,40%5D,%22crypto-md5%22:%5B22,22,23,22,22%5D,%22crypto-sha1%22:%5B12,12,12,12,12%5D,%22date-format-tofte%22:%5B122,116,119,119,121%5D,%22date-format-xparb%22:%5B98,100,99,99,101%5D,%22math-cordic%22:%5B38,39,39,39,39%5D,%22math-partial-sums%22:%5B29,39,29,29,30%5D,%22math-spectral-norm%22:%5B11,8,10,8,9%5D,%22regexp-dna%22:%5B96,94,95,80,93%5D,%22string-base64%22:%5B25,24,24,25,25%5D,%22string-fasta%22:%5B119,111,113,113,114%5D,%22string-tagcloud%22:%5B132,132,131,132,130%5D,%22string-unpack-code%22:%5B162,160,163,162,163%5D,%22string-validate-input%22:%5B54,55,50,55,52%5D%7D](http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B63,62,62,63,62%5D,%223d-morph%22:%5B46,40,41,41,47%5D,%223d-raytrace%22:%5B102,102,99,99,100%5D,%22access-binary-trees%22:%5B53,52,53,54,53%5D,%22access-fannkuch%22:%5B77,77,77,77,85%5D,%22access-nbody%22:%5B36,35,34,34,36%5D,%22access-nsieve%22:%5B15,15,14,15,16%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,2,1%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,2,3,3,2%5D,%22bitops-nsieve-bits%22:%5B37,37,35,35,35%5D,%22controlflow-recursive%22:%5B45,43,44,44,43%5D,%22crypto-aes%22:%5B47,44,47,43,40%5D,%22crypto-md5%22:%5B22,22,23,22,22%5D,%22crypto-sha1%22:%5B12,12,12,12,12%5D,%22date-format-tofte%22:%5B122,116,119,119,121%5D,%22date-format-xparb%22:%5B98,100,99,99,101%5D,%22math-cordic%22:%5B38,39,39,39,39%5D,%22math-partial-sums%22:%5B29,39,29,29,30%5D,%22math-spectral-norm%22:%5B11,8,10,8,9%5D,%22regexp-dna%22:%5B96,94,95,80,93%5D,%22string-base64%22:%5B25,24,24,25,25%5D,%22string-fasta%22:%5B119,111,113,113,114%5D,%22string-tagcloud%22:%5B132,132,131,132,130%5D,%22string-unpack-code%22:%5B162,160,163,162,163%5D,%22string-validate-input%22:%5B54,55,50,55,52%5D%7D)

Firefox 3.5 PGO: [http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B56,56,56,55,57%5D,%223d-morph%22:%5B33,32,40,32,32%5D,%223d-raytrace%22:%5B82,82,82,82,83%5D,%22access-binary-trees%22:%5B48,48,48,48,48%5D,%22access-fannkuch%22:%5B62,74,74,60,60%5D,%22access-nbody%22:%5B29,29,29,29,29%5D,%22access-nsieve%22:%5B13,13,13,13,13%5D,%22bitops-3bit-bits-in-byte%22:%5B1,2,1,2,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,3,2,2,2%5D,%22bitops-nsieve-bits%22:%5B30,30,30,30,30%5D,%22controlflow-recursive%22:%5B39,39,39,38,38%5D,%22crypto-aes%22:%5B37,38,41,39,38%5D,%22crypto-md5%22:%5B19,19,19,19,19%5D,%22crypto-sha1%22:%5B10,10,9,10,9%5D,%22date-format-tofte%22:%5B101,100,100,100,98%5D,%22date-format-xparb%22:%5B77,78,78,78,78%5D,%22math-cordic%22:%5B21,20,20,21,21%5D,%22math-partial-sums%22:%5B29,29,28,28,29%5D,%22math-spectral-norm%22:%5B10,8,8,8,8%5D,%22regexp-dna%22:%5B102,101,102,98,95%5D,%22string-base64%22:%5B18,18,18,18,18%5D,%22string-fasta%22:%5B91,90,90,90,90%5D,%22string-tagcloud%22:%5B110,117,116,115,117%5D,%22string-unpack-code%22:%5B134,138,137,140,139%5D,%22string-validate-input%22:%5B48,44,44,48,45%5D%7D](http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B56,56,56,55,57%5D,%223d-morph%22:%5B33,32,40,32,32%5D,%223d-raytrace%22:%5B82,82,82,82,83%5D,%22access-binary-trees%22:%5B48,48,48,48,48%5D,%22access-fannkuch%22:%5B62,74,74,60,60%5D,%22access-nbody%22:%5B29,29,29,29,29%5D,%22access-nsieve%22:%5B13,13,13,13,13%5D,%22bitops-3bit-bits-in-byte%22:%5B1,2,1,2,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,3,2,2,2%5D,%22bitops-nsieve-bits%22:%5B30,30,30,30,30%5D,%22controlflow-recursive%22:%5B39,39,39,38,38%5D,%22crypto-aes%22:%5B37,38,41,39,38%5D,%22crypto-md5%22:%5B19,19,19,19,19%5D,%22crypto-sha1%22:%5B10,10,9,10,9%5D,%22date-format-tofte%22:%5B101,100,100,100,98%5D,%22date-format-xparb%22:%5B77,78,78,78,78%5D,%22math-cordic%22:%5B21,20,20,21,21%5D,%22math-partial-sums%22:%5B29,29,28,28,29%5D,%22math-spectral-norm%22:%5B10,8,8,8,8%5D,%22regexp-dna%22:%5B102,101,102,98,95%5D,%22string-base64%22:%5B18,18,18,18,18%5D,%22string-fasta%22:%5B91,90,90,90,90%5D,%22string-tagcloud%22:%5B110,117,116,115,117%5D,%22string-unpack-code%22:%5B134,138,137,140,139%5D,%22string-validate-input%22:%5B48,44,44,48,45%5D%7D)

Firefox 3.5 Windows in Wine: [http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B47,50,48,49,49%5D,%223d-morph%22:%5B56,56,56,56,56%5D,%223d-raytrace%22:%5B79,78,79,78,79%5D,%22access-binary-trees%22:%5B46,44,44,45,45%5D,%22access-fannkuch%22:%5B68,67,68,70,70%5D,%22access-nbody%22:%5B28,27,28,28,28%5D,%22access-nsieve%22:%5B12,13,13,13,14%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,1,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B3,4,3,2,3%5D,%22bitops-nsieve-bits%22:%5B28,28,27,28,28%5D,%22controlflow-recursive%22:%5B39,40,47,40,39%5D,%22crypto-aes%22:%5B41,37,38,38,41%5D,%22crypto-md5%22:%5B19,18,18,19,18%5D,%22crypto-sha1%22:%5B9,10,10,9,10%5D,%22date-format-tofte%22:%5B121,117,118,122,118%5D,%22date-format-xparb%22:%5B143,141,143,145,143%5D,%22math-cordic%22:%5B33,33,33,33,33%5D,%22math-partial-sums%22:%5B19,21,18,18,18%5D,%22math-spectral-norm%22:%5B8,8,8,8,8%5D,%22regexp-dna%22:%5B104,92,81,93,67%5D,%22string-base64%22:%5B17,17,18,18,18%5D,%22string-fasta%22:%5B86,84,81,84,83%5D,%22string-tagcloud%22:%5B103,104,117,107,95%5D,%22string-unpack-code%22:%5B138,135,141,136,136%5D,%22string-validate-input%22:%5B46,43,47,43,42%5D%7D](http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B47,50,48,49,49%5D,%223d-morph%22:%5B56,56,56,56,56%5D,%223d-raytrace%22:%5B79,78,79,78,79%5D,%22access-binary-trees%22:%5B46,44,44,45,45%5D,%22access-fannkuch%22:%5B68,67,68,70,70%5D,%22access-nbody%22:%5B28,27,28,28,28%5D,%22access-nsieve%22:%5B12,13,13,13,14%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,1,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B3,4,3,2,3%5D,%22bitops-nsieve-bits%22:%5B28,28,27,28,28%5D,%22controlflow-recursive%22:%5B39,40,47,40,39%5D,%22crypto-aes%22:%5B41,37,38,38,41%5D,%22crypto-md5%22:%5B19,18,18,19,18%5D,%22crypto-sha1%22:%5B9,10,10,9,10%5D,%22date-format-tofte%22:%5B121,117,118,122,118%5D,%22date-format-xparb%22:%5B143,141,143,145,143%5D,%22math-cordic%22:%5B33,33,33,33,33%5D,%22math-partial-sums%22:%5B19,21,18,18,18%5D,%22math-spectral-norm%22:%5B8,8,8,8,8%5D,%22regexp-dna%22:%5B104,92,81,93,67%5D,%22string-base64%22:%5B17,17,18,18,18%5D,%22string-fasta%22:%5B86,84,81,84,83%5D,%22string-tagcloud%22:%5B103,104,117,107,95%5D,%22string-unpack-code%22:%5B138,135,141,136,136%5D,%22string-validate-input%22:%5B46,43,47,43,42%5D%7D)

These preform about the same, which is due to PGO (Windows build has pgo, Linux default is not pgo*).  Without PGO, Firefox will lag behind even firefox in wine in javascript preformance.
See: [http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox](http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox)

*If I recall correctly
I think PGO makes a difference.  Is a 200ms difference perceivable?  I think in some javascript heavy tasks it might be.

---

### Post by Andy06 on 2009-07-05
```
swiftfox -P
```

and

```
swiftfox profilename
```

did not work. I wanted to launch the profile manager from swiftfox itself so that I could change location of its profile from within its profile manager without having to resort to a custom -"swiftfox pofile" switch. I guess I will just use the Firefox Profile manager to do that now.

Thanks

---

### Post by darco on 2009-07-05
> **l-x-l said:**
> The FF plugins are installed in ~/.mozilla/plugins. I already tried copying them to /usr/lib/swiftfox/plugins as well as /usr/lib64/swiftfox/plugins. Neither of which worked for me. I posted a msg in the swiftfox forums & have never gotten a response. If you can think of any other location I could try, please let me know.

Ok, I too am running x64 and after hunting around on the SF Forum, the admin wrote this:  "Another thing to keep in mind, Swiftfox is 32bit, it won't use 64bit plugins. If you are using 64bit plugins that explains why Swiftfox isn't finding any"

darco

---

### Post by lovinglinux on 2009-07-05
> **shae said:**
> Firefox 3.5 without PGO(official from site): [http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B63,62,62,63,62%5D,%223d-morph%22:%5B46,40,41,41,47%5D,%223d-raytrace%22:%5B102,102,99,99,100%5D,%22access-binary-trees%22:%5B53,52,53,54,53%5D,%22access-fannkuch%22:%5B77,77,77,77,85%5D,%22access-nbody%22:%5B36,35,34,34,36%5D,%22access-nsieve%22:%5B15,15,14,15,16%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,2,1%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,2,3,3,2%5D,%22bitops-nsieve-bits%22:%5B37,37,35,35,35%5D,%22controlflow-recursive%22:%5B45,43,44,44,43%5D,%22crypto-aes%22:%5B47,44,47,43,40%5D,%22crypto-md5%22:%5B22,22,23,22,22%5D,%22crypto-sha1%22:%5B12,12,12,12,12%5D,%22date-format-tofte%22:%5B122,116,119,119,121%5D,%22date-format-xparb%22:%5B98,100,99,99,101%5D,%22math-cordic%22:%5B38,39,39,39,39%5D,%22math-partial-sums%22:%5B29,39,29,29,30%5D,%22math-spectral-norm%22:%5B11,8,10,8,9%5D,%22regexp-dna%22:%5B96,94,95,80,93%5D,%22string-base64%22:%5B25,24,24,25,25%5D,%22string-fasta%22:%5B119,111,113,113,114%5D,%22string-tagcloud%22:%5B132,132,131,132,130%5D,%22string-unpack-code%22:%5B162,160,163,162,163%5D,%22string-validate-input%22:%5B54,55,50,55,52%5D%7D](http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B63,62,62,63,62%5D,%223d-morph%22:%5B46,40,41,41,47%5D,%223d-raytrace%22:%5B102,102,99,99,100%5D,%22access-binary-trees%22:%5B53,52,53,54,53%5D,%22access-fannkuch%22:%5B77,77,77,77,85%5D,%22access-nbody%22:%5B36,35,34,34,36%5D,%22access-nsieve%22:%5B15,15,14,15,16%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,2,1%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,2,3,3,2%5D,%22bitops-nsieve-bits%22:%5B37,37,35,35,35%5D,%22controlflow-recursive%22:%5B45,43,44,44,43%5D,%22crypto-aes%22:%5B47,44,47,43,40%5D,%22crypto-md5%22:%5B22,22,23,22,22%5D,%22crypto-sha1%22:%5B12,12,12,12,12%5D,%22date-format-tofte%22:%5B122,116,119,119,121%5D,%22date-format-xparb%22:%5B98,100,99,99,101%5D,%22math-cordic%22:%5B38,39,39,39,39%5D,%22math-partial-sums%22:%5B29,39,29,29,30%5D,%22math-spectral-norm%22:%5B11,8,10,8,9%5D,%22regexp-dna%22:%5B96,94,95,80,93%5D,%22string-base64%22:%5B25,24,24,25,25%5D,%22string-fasta%22:%5B119,111,113,113,114%5D,%22string-tagcloud%22:%5B132,132,131,132,130%5D,%22string-unpack-code%22:%5B162,160,163,162,163%5D,%22string-validate-input%22:%5B54,55,50,55,52%5D%7D)

Firefox 3.5 PGO: [http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B56,56,56,55,57%5D,%223d-morph%22:%5B33,32,40,32,32%5D,%223d-raytrace%22:%5B82,82,82,82,83%5D,%22access-binary-trees%22:%5B48,48,48,48,48%5D,%22access-fannkuch%22:%5B62,74,74,60,60%5D,%22access-nbody%22:%5B29,29,29,29,29%5D,%22access-nsieve%22:%5B13,13,13,13,13%5D,%22bitops-3bit-bits-in-byte%22:%5B1,2,1,2,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,3,2,2,2%5D,%22bitops-nsieve-bits%22:%5B30,30,30,30,30%5D,%22controlflow-recursive%22:%5B39,39,39,38,38%5D,%22crypto-aes%22:%5B37,38,41,39,38%5D,%22crypto-md5%22:%5B19,19,19,19,19%5D,%22crypto-sha1%22:%5B10,10,9,10,9%5D,%22date-format-tofte%22:%5B101,100,100,100,98%5D,%22date-format-xparb%22:%5B77,78,78,78,78%5D,%22math-cordic%22:%5B21,20,20,21,21%5D,%22math-partial-sums%22:%5B29,29,28,28,29%5D,%22math-spectral-norm%22:%5B10,8,8,8,8%5D,%22regexp-dna%22:%5B102,101,102,98,95%5D,%22string-base64%22:%5B18,18,18,18,18%5D,%22string-fasta%22:%5B91,90,90,90,90%5D,%22string-tagcloud%22:%5B110,117,116,115,117%5D,%22string-unpack-code%22:%5B134,138,137,140,139%5D,%22string-validate-input%22:%5B48,44,44,48,45%5D%7D](http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B56,56,56,55,57%5D,%223d-morph%22:%5B33,32,40,32,32%5D,%223d-raytrace%22:%5B82,82,82,82,83%5D,%22access-binary-trees%22:%5B48,48,48,48,48%5D,%22access-fannkuch%22:%5B62,74,74,60,60%5D,%22access-nbody%22:%5B29,29,29,29,29%5D,%22access-nsieve%22:%5B13,13,13,13,13%5D,%22bitops-3bit-bits-in-byte%22:%5B1,2,1,2,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B2,3,2,2,2%5D,%22bitops-nsieve-bits%22:%5B30,30,30,30,30%5D,%22controlflow-recursive%22:%5B39,39,39,38,38%5D,%22crypto-aes%22:%5B37,38,41,39,38%5D,%22crypto-md5%22:%5B19,19,19,19,19%5D,%22crypto-sha1%22:%5B10,10,9,10,9%5D,%22date-format-tofte%22:%5B101,100,100,100,98%5D,%22date-format-xparb%22:%5B77,78,78,78,78%5D,%22math-cordic%22:%5B21,20,20,21,21%5D,%22math-partial-sums%22:%5B29,29,28,28,29%5D,%22math-spectral-norm%22:%5B10,8,8,8,8%5D,%22regexp-dna%22:%5B102,101,102,98,95%5D,%22string-base64%22:%5B18,18,18,18,18%5D,%22string-fasta%22:%5B91,90,90,90,90%5D,%22string-tagcloud%22:%5B110,117,116,115,117%5D,%22string-unpack-code%22:%5B134,138,137,140,139%5D,%22string-validate-input%22:%5B48,44,44,48,45%5D%7D)

Firefox 3.5 Windows in Wine: [http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B47,50,48,49,49%5D,%223d-morph%22:%5B56,56,56,56,56%5D,%223d-raytrace%22:%5B79,78,79,78,79%5D,%22access-binary-trees%22:%5B46,44,44,45,45%5D,%22access-fannkuch%22:%5B68,67,68,70,70%5D,%22access-nbody%22:%5B28,27,28,28,28%5D,%22access-nsieve%22:%5B12,13,13,13,14%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,1,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B3,4,3,2,3%5D,%22bitops-nsieve-bits%22:%5B28,28,27,28,28%5D,%22controlflow-recursive%22:%5B39,40,47,40,39%5D,%22crypto-aes%22:%5B41,37,38,38,41%5D,%22crypto-md5%22:%5B19,18,18,19,18%5D,%22crypto-sha1%22:%5B9,10,10,9,10%5D,%22date-format-tofte%22:%5B121,117,118,122,118%5D,%22date-format-xparb%22:%5B143,141,143,145,143%5D,%22math-cordic%22:%5B33,33,33,33,33%5D,%22math-partial-sums%22:%5B19,21,18,18,18%5D,%22math-spectral-norm%22:%5B8,8,8,8,8%5D,%22regexp-dna%22:%5B104,92,81,93,67%5D,%22string-base64%22:%5B17,17,18,18,18%5D,%22string-fasta%22:%5B86,84,81,84,83%5D,%22string-tagcloud%22:%5B103,104,117,107,95%5D,%22string-unpack-code%22:%5B138,135,141,136,136%5D,%22string-validate-input%22:%5B46,43,47,43,42%5D%7D](http://www2.webkit.org/perf/sunspider-0.9/sunspider-results.html?%7B%223d-cube%22:%5B47,50,48,49,49%5D,%223d-morph%22:%5B56,56,56,56,56%5D,%223d-raytrace%22:%5B79,78,79,78,79%5D,%22access-binary-trees%22:%5B46,44,44,45,45%5D,%22access-fannkuch%22:%5B68,67,68,70,70%5D,%22access-nbody%22:%5B28,27,28,28,28%5D,%22access-nsieve%22:%5B12,13,13,13,14%5D,%22bitops-3bit-bits-in-byte%22:%5B2,1,1,1,2%5D,%22bitops-bits-in-byte%22:%5B9,9,9,9,9%5D,%22bitops-bitwise-and%22:%5B3,4,3,2,3%5D,%22bitops-nsieve-bits%22:%5B28,28,27,28,28%5D,%22controlflow-recursive%22:%5B39,40,47,40,39%5D,%22crypto-aes%22:%5B41,37,38,38,41%5D,%22crypto-md5%22:%5B19,18,18,19,18%5D,%22crypto-sha1%22:%5B9,10,10,9,10%5D,%22date-format-tofte%22:%5B121,117,118,122,118%5D,%22date-format-xparb%22:%5B143,141,143,145,143%5D,%22math-cordic%22:%5B33,33,33,33,33%5D,%22math-partial-sums%22:%5B19,21,18,18,18%5D,%22math-spectral-norm%22:%5B8,8,8,8,8%5D,%22regexp-dna%22:%5B104,92,81,93,67%5D,%22string-base64%22:%5B17,17,18,18,18%5D,%22string-fasta%22:%5B86,84,81,84,83%5D,%22string-tagcloud%22:%5B103,104,117,107,95%5D,%22string-unpack-code%22:%5B138,135,141,136,136%5D,%22string-validate-input%22:%5B46,43,47,43,42%5D%7D)

These preform about the same, which is due to PGO (Windows build has pgo, Linux default is not pgo*).  Without PGO, Firefox will lag behind even firefox in wine in javascript preformance.
See: [http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox](http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox)

*If I recall correctly
I think PGO makes a difference.  Is a 200ms difference perceivable?  I think in some javascript heavy tasks it might be.


I just compiled Firefox with PGO enabled. The processor optimizations gives 30% performance boost, but I can't see the difference with PGO. I will make more benchmark tests and post the results.

---

### Post by l-x-l on 2009-07-05
> **darco said:**
> Ok, I too am running x64 and after hunting around on the SF Forum, the admin wrote this:  "Another thing to keep in mind, Swiftfox is 32bit, it won't use 64bit plugins. If you are using 64bit plugins that explains why Swiftfox isn't finding any"

darco

Thanks. That's probably the issue I'm having. Oh well since FF 3.5 has come out, I've gone back to using that.

---

### Post by lovinglinux on 2009-07-05
> **lovinglinux said:**
> I just compiled Firefox with PGO enabled. The processor optimizations gives 30% performance boost, but I can't see the difference with PGO. I will make more benchmark tests and post the results.

I did the tests and actually there is an improvement, but not much.

Firefox 3.5 with extensions/without pgo - 872 points
Firefox 3.5 with extensions/with pgo - 936 points

Firefox 3.5 without extensions/without pgo - 1082 points
Firefox 3.5 without extensions/with pgo - 1113 points

---

### Post by shae on 2009-07-05
What do you use to benchmark?  My understanding that the majority of the benefits of PGO are in its improvement in the speed of javascript execution.

---

### Post by lovinglinux on 2009-07-05
> **shae said:**
> What do you use to benchmark?  My understanding that the majority of the benefits of PGO are in its improvement in the speed of javascript execution.

[Peacekeeper](http://service.futuremark.com/peacekeeper/index.action)

You can see my benchmarks and tips to improve performance in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

