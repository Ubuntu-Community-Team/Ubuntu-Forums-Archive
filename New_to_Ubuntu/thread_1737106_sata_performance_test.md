---
title: "sata performance test"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by zu1u on 2011-04-23
I just used iozone to see how fast my new SATA drive is and I get  2129853.66 KB/s for read. This is about 16.25 Gb/s if i'm not mistaken. 
SATA does 1.5, 3 or 6 Gb/s, depending on the revision. Can someone help me in where I might be making a mistake there?

---

### Post by mr_luksom on 2011-04-23
Doesn't sound right. What results do you get from hdparm?

```

sudo hdparm -Tt /dev/sda1

```

Substitute /dev/sda1 for the device you want to test.

---

### Post by zu1u on 2011-04-23
With hdparm I get:
Timing cached reads 1274 MB in 2.00 seconds = 636.47 MB/sec
Timing buffered disk reads: 138 MB in 3.04 seconds = 45.39 MB/sec

Any idea why I get so different values with iozone?
here's an output of iozone:
```

Iozone: Performance Test of File I/O
	        Version $Revision: 3.308 $
		Compiled for 64 bit mode.
		Build: linux 

	Contributors:William Norcott, Don Capps, Isom Crawford, Kirby Collins
	             Al Slater, Scott Rhine, Mike Wisner, Ken Goss
	             Steve Landherr, Brad Smith, Mark Kelly, Dr. Alain CYR,
	             Randy Dunlap, Mark Montague, Dan Million, Gavin Brebner,
	             Jean-Marc Zucconi, Jeff Blomberg, Benny Halevy,
	             Erik Habbinga, Kris Strecker, Walter Wong, Joshua Root.

	Run began: Fri Apr 22 00:04:40 2011

	File size set to 51200 KB
	Excel chart generation enabled
	Command line used: iozone -l 5 -u 5 -s 50m -R -b /tmp/1/550.xls -F /media/TEST/f1 /media/TEST/f2 /media/TEST/f3 /media/TEST/f4 /media/TEST/f5
	Output is in Kbytes/sec
	Time Resolution = 0.000001 seconds.
	Processor cache size set to 1024 Kbytes.
	Processor cache line size set to 32 bytes.
	File stride size set to 17 * record size.
	Min process = 5 
	Max process = 5 
	Throughput test with 5 processes
	Each process writes a 51200 Kbyte file in 4 Kbyte records

	Children see throughput for  5 initial writers 	=  246059.19 KB/sec
	Parent sees throughput for  5 initial writers 	=   21110.12 KB/sec
	Min throughput per process 			=   38150.23 KB/sec 
	Max throughput per process 			=   76263.33 KB/sec
	Avg throughput per process 			=   49211.84 KB/sec
	Min xfer 					=   25556.00 KB

	Children see throughput for  5 rewriters 	=   86058.34 KB/sec
	Parent sees throughput for  5 rewriters 	=   29796.33 KB/sec
	Min throughput per process 			=   15701.09 KB/sec 
	Max throughput per process 			=   19563.46 KB/sec
	Avg throughput per process 			=   17211.67 KB/sec
	Min xfer 					=   41600.00 KB

	Children see throughput for  5 readers 		= 2089045.09 KB/sec
	Parent sees throughput for  5 readers 		= 1530333.07 KB/sec
	Min throughput per process 			=  257287.72 KB/sec 
	Max throughput per process 			=  518539.50 KB/sec
	Avg throughput per process 			=  417809.02 KB/sec
	Min xfer 					=   25420.00 KB

	Children see throughput for 5 re-readers 	= 2055142.27 KB/sec
	Parent sees throughput for 5 re-readers 	= 1942542.78 KB/sec
	Min throughput per process 			=  258901.64 KB/sec 
	Max throughput per process 			=  516791.22 KB/sec
	Avg throughput per process 			=  411028.45 KB/sec
	Min xfer 					=   20780.00 KB

	Children see throughput for 5 reverse readers 	= 1839414.62 KB/sec
	Parent sees throughput for 5 reverse readers 	= 1748394.98 KB/sec
	Min throughput per process 			=  229040.03 KB/sec 
	Max throughput per process 			=  459419.84 KB/sec
	Avg throughput per process 			=  367882.92 KB/sec
	Min xfer 					=   22128.00 KB

	Children see throughput for 5 stride readers 	= 1779844.83 KB/sec
	Parent sees throughput for 5 stride readers 	= 1707344.19 KB/sec
	Min throughput per process 			=  224870.16 KB/sec 
	Max throughput per process 			=  440036.66 KB/sec
	Avg throughput per process 			=  355968.97 KB/sec
	Min xfer 					=   23080.00 KB

	Children see throughput for 5 random readers 	= 1850449.30 KB/sec
	Parent sees throughput for 5 random readers 	= 1759874.59 KB/sec
	Min throughput per process 			=  227014.33 KB/sec 
	Max throughput per process 			=  454537.38 KB/sec
	Avg throughput per process 			=  370089.86 KB/sec
	Min xfer 					=   25196.00 KB

	Children see throughput for 5 mixed workload 	= 1135221.11 KB/sec
	Parent sees throughput for 5 mixed workload 	=   33978.11 KB/sec
	Min throughput per process 			=   91808.22 KB/sec 
	Max throughput per process 			=  449924.38 KB/sec
	Avg throughput per process 			=  227044.22 KB/sec
	Min xfer 					=   10452.00 KB

	Children see throughput for 5 random writers 	=   88760.41 KB/sec
	Parent sees throughput for 5 random writers 	=   19230.19 KB/sec
	Min throughput per process 			=    5675.97 KB/sec 
	Max throughput per process 			=   46042.00 KB/sec
	Avg throughput per process 			=   17752.08 KB/sec
	Min xfer 					=   31016.00 KB

	Children see throughput for 5 pwrite writers 	=  243020.93 KB/sec
	Parent sees throughput for 5 pwrite writers 	=   21605.33 KB/sec
	Min throughput per process 			=   37228.33 KB/sec 
	Max throughput per process 			=   66851.22 KB/sec
	Avg throughput per process 			=   48604.19 KB/sec
	Min xfer 					=   29084.00 KB

	Children see throughput for 5 pread readers 	= 1598297.62 KB/sec
	Parent sees throughput for 5 pread readers 	= 1222923.59 KB/sec
	Min throughput per process 			=  193488.20 KB/sec 
	Max throughput per process 			=  393864.72 KB/sec
	Avg throughput per process 			=  319659.53 KB/sec
	Min xfer 					=   25192.00 KB



"Throughput report Y-axis is type of test X-axis is number of processes"
"Record size = 4 Kbytes "
"Output is in Kbytes/sec"

"  Initial write "  246059.19 

"        Rewrite "   86058.34 

"           Read " 2089045.09 

"        Re-read " 2055142.27 

"   Reverse Read " 1839414.62 

"    Stride read " 1779844.83 

"    Random read " 1850449.30 

" Mixed workload " 1135221.11 

"   Random write "   88760.41 

"         Pwrite "  243020.93 

"          Pread " 1598297.62 


iozone test complete.

```

---

