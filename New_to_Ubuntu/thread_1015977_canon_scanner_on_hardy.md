---
title: "canon scanner on hardy"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by koba101 on 2008-12-19
Hi,

I just bought a cheap canon scanner that looks cool. I'm trying to get it to work.  

 i get this output when running san-find-scanner

```

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9, product=0x1904, chip=GL843?) at libusb:007:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

but scanimage -L generates the following


```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

any tips? suggestions?  would it be wise to return this scanner?

---

### Post by cariboo on 2008-12-19
Canon has stated they will not support linux, so I would suggest returning your scanner and check [here]("http://www.sane-project.org/sane-mfgs.html") for supported scaners. Purchase one that is well supported.

Jim

---

### Post by koba101 on 2008-12-20
what a shame...the scanner looks great, and i've been looking for a stand-alone scanner forever

---

