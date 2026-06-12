---
title: "intel core i5-750 lynnfield i7 performance/utils/benchmarks"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by daimaru on 2010-05-16
Hi

I'm wondering if there are any special utilities or tweaks for the intel core i5-750 series CPUs? I am trying to figure out if my cpu is preforming as it should. I guess it does, but since I don't have any way to monitor the cpu frequency I am not sure.

If I try adding "CPU Frequency Scaling Monitor" applet to the panel I get the error message "CPU frequency scaling unsupported". (see attachment)

I installed cpufrequtils and ran cpufreq-info but had no luck there either.
```
cpufreq-info 
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
```I ran a few benchmarks from the Phoronix Test Suite and compared my results to those the posted in their article on the lynnfield processors. You can get the test suite and documentation [here]("http://www.phoronix-test-suite.com/") . Or install using aptiude or synaptic:
```
sudo apt-get install phoronix-test-suite
```Check out their article on the i5 processor [here]("http://www.phoronix.com/scan.php?page=article&item=intel_lynnfield_add&num=1") . I only ran  john-the-ripper, encode-mp3 and nexuiz benchmarks up till now. But if anyone knows the test suite and knows which benchmarks are best for testing the cpu then post those results with the name of the benchmark one has to run and I will post my results from those too.

How the Test suite works:
```
phoronix-test-suite list-tests
```shows a list of all available tests.
```
phoronix-test-suite info <testname>
```shows detailed info for selected benchmark test
```
phoronix-test-suite benchmark <testname>
```downloads needed test files and starts the test. 

I choose No on the save results question.
These are the test I ran:
```
gg@alita:~$phoronix-test-suite benchmark john-the-ripper
      john-the-ripper [Test: Traditional DES]
      Average: 3521667 Real C/S

      john-the-ripper [Test: MD5]
      Average: 16643 Real C/S

      john-the-ripper [Test: Blowfish]
      Average: 967 Real C/S

``````
gg@alita:~$phoronix-test-suite benchmark encode-mp3
LAME MP3 Encoding:
      encode-mp3
      Average: 22.57 Seconds

```mplayer build benchmark
```
gg@alita:~$phoronix-test-suite benchmark build-mplayer
      Average: 16.39 Seconds

```watch out the nexuiz is an 800mb download and I guess it won't help much with cpu since you need a good graphics card too.
```
gg@alita:~$phoronix-test-suite benchmark nexuiz
Nexuiz:
      nexuiz [Resolution: 1920 x 1200 - HDR: Yes - Sound: On]
      Average: 134.51 Frames Per Second

```If anyone else has an i5 or i7 processor feel free to post your  benchmark results for comparison in your replies. And if you know any tools that can monitor i5 i7 cpus post them too. Thanks

---

### Post by hunkgagan on 2010-05-16
Hi, I am newbie.

I have core i7. Please tell me the simple procedure to do this.

---

### Post by daimaru on 2010-05-16
open terminal (Applications->Accessories->Terminal) and type in the following commands.
to install the benchmark suite: (you can highlight the code with your mouse and then switch to your console and middle mouse click to copy paste|or right click copy paste)
```
sudo apt-get install phoronix-test-suite
```to install and run the john-the-ripper password decryption benchmark:
```
phoronix-test-suite benchmark john-the-ripper
```for Lame mp3 encoding benchmark:
```
phoronix-test-suite benchmark encode-mp3
```
for mplayer compiling benchmark
```
phoronix-test-suite benchmark build-mplayer
```
for nexuiz (1st person shooter - 800 mb download) 
```
phoronix-test-suite benchmark nexuiz
```hope this helps

---

