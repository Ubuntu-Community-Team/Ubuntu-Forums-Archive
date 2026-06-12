---
title: "PPPD prob"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by gaf.stephanos on 2008-10-25
Hi all, I have an HSFMODEM by Conexant on my laptop.
I installed Ubuntu on it and then the Linuxant drivers. 
They work great. 
I know that because they give the same sounds like on windows and the modem accepts the AT commands. 
Anyway, I tried all dial-up progs on ubuntu. 
In wvdial, it connects and after the CONNECT line from the modem, it gives some strange text which pppd doesn't handle. 
At the beginning I thought that was something wrong with the driver but I searched everywhere for a port monitor on windows and found Portmon.exe from SysInternals and got a log. It's attached. I found that text to be actually authentication prompts and MSRAS on windows replies and establishes the connection but pppd doesn't do that. I replaced my username and password with "USERNAME" and "PASSWORD" in the log (I don't want anyone to know them of course :P). It's attached. Can anyone help please ?
If anyone wants to know, I live in Oman and that connection is from Omantel.

---

### Post by gaf.stephanos on 2008-10-27
Is anyone able to help ? Please, it's urgent. Is there something missing in my last post ?

---

### Post by eder.apt-get on 2008-10-27
Post the "strange test that pppd doesn´t handle" here. It may be useful for someone who wants to help you out.

---

### Post by gaf.stephanos on 2008-10-27
OK, here's the log if it's easier for people who don't want to download attachments. It's the same as the attachment.

2	0.13677430	svchost.exe	IRP_MJ_CREATE			Winachsf0	SUCCESS	Options: Open 	
3	0.00013221	svchost.exe	IOCTL_SERIAL_GET_PROPERTIES	Winachsf0	SUCCESS		
4	0.00000258	svchost.exe	IOCTL_SERIAL_SET_COMMCONFIG	Winachsf0	SUCCESS		
5	0.00000196	svchost.exe	IOCTL_SERIAL_GET_BAUD_RATE	Winachsf0	SUCCESS		
6	0.00000147	svchost.exe	IOCTL_SERIAL_GET_LINE_CONTROL	Winachsf0	SUCCESS		
7	0.00000140	svchost.exe	IOCTL_SERIAL_GET_CHARS		Winachsf0	SUCCESS		
8	0.00000140	svchost.exe	IOCTL_SERIAL_GET_HANDFLOW	Winachsf0	SUCCESS		
9	0.00000356	svchost.exe	IOCTL_SERIAL_SET_BAUD_RATE	Winachsf0	SUCCESS	Rate: 115200	
10	0.00000223	svchost.exe	IOCTL_SERIAL_SET_DTR		Winachsf0	SUCCESS		
11	0.00000182	svchost.exe	IOCTL_SERIAL_SET_LINE_CONTROL	Winachsf0	SUCCESS	StopBits: 1 Parity: NONE WordLength: 8	
12	0.00000196	svchost.exe	IOCTL_SERIAL_SET_CHAR		Winachsf0	SUCCESS	EOF:0 ERR:0 BRK:0 EVT:0 XON:11 XOFF:13	
13	0.00000182	svchost.exe	IOCTL_SERIAL_SET_HANDFLOW	Winachsf0	SUCCESS	Shake:9 Replace:80 XonLimit:10 XoffLimit:10	
14	0.00001222	svchost.exe	IRP_MJ_DEVICE_CONTROL		Winachsf0	SUCCESS	IOCTL: 0x2B0008	
15	0.00000196	svchost.exe	IOCTL_SERIAL_CLEAR_STATS	Winachsf0	SUCCESS		
16	0.00000461	svchost.exe	IOCTL_SERIAL_PURGE		Winachsf0	SUCCESS	Purge: RXABORT 	
17	0.00000189	svchost.exe	IOCTL_SERIAL_SET_TIMEOUTS	Winachsf0	SUCCESS	RI:20 RM:0 RC:0 WM:10 WC:2000	
18	0.00000182	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
19	0.01133286	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
20	0.00000175	svchost.exe	IOCTL_SERIAL_SET_COMMCONFIG	Winachsf0	SUCCESS		
21	0.00000168	svchost.exe	IOCTL_SERIAL_GET_BAUD_RATE	Winachsf0	SUCCESS		
22	0.00000154	svchost.exe	IOCTL_SERIAL_GET_LINE_CONTROL	Winachsf0	SUCCESS		
23	0.00000154	svchost.exe	IOCTL_SERIAL_GET_CHARS		Winachsf0	SUCCESS		
24	0.00000140	svchost.exe	IOCTL_SERIAL_GET_HANDFLOW	Winachsf0	SUCCESS		
25	0.00000370	svchost.exe	IOCTL_SERIAL_SET_BAUD_RATE	Winachsf0	SUCCESS	Rate: 115200	
26	0.00000217	svchost.exe	IOCTL_SERIAL_SET_DTR		Winachsf0	SUCCESS		
27	0.00000175	svchost.exe	IOCTL_SERIAL_SET_LINE_CONTROL	Winachsf0	SUCCESS	StopBits: 1 Parity: NONE WordLength: 8	
28	0.00000203	svchost.exe	IOCTL_SERIAL_SET_CHAR		Winachsf0	SUCCESS	EOF:0 ERR:0 BRK:0 EVT:0 XON:11 XOFF:13	
29	0.00000182	svchost.exe	IOCTL_SERIAL_SET_HANDFLOW	Winachsf0	SUCCESS	Shake:9 Replace:80 XonLimit:10 XoffLimit:10	
30	0.00000161	svchost.exe	IOCTL_SERIAL_SET_DTR		Winachsf0	SUCCESS		
31	0.00000237	svchost.exe	IOCTL_SERIAL_GET_MODEMSTATUS	Winachsf0	SUCCESS		
32	0.00089236	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 3: AT.	
33	0.00000314	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
34	0.00000363	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
35	0.00000217	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
36	0.01220267	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
37	0.00086778	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 39: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2.	
38	0.00000433	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
39	0.00000391	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
40	0.00000203	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
41	0.01008620	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
42	0.00081959	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 52: ATS7=60S30=0L2M1+ES=3,0,2;+DS=3;+DS44=3;+IFC=2,2;X4.	
43	0.00000335	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
44	0.00000356	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
45	0.00000203	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
46	0.03203899	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
47	0.00085416	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 10: at+vcid=1.	
48	0.00000405	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
49	0.00000398	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
50	0.00000210	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
51	0.01050441	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
52	0.00017844	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 7: ATS0=0.	
53	0.00000286	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
54	0.00000363	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
55	0.00000217	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
56	0.01680360	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
57	0.00000356	svchost.exe	IOCTL_SERIAL_SET_WAIT_MASK	Winachsf0	SUCCESS	Mask: DSR 	
58	0.00661599	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
59	0.00000168	svchost.exe	IRP_MJ_DEVICE_CONTROL		Winachsf0	SUCCESS	IOCTL: 0x2B0030	
60	0.00000000	svchost.exe	IRP_MJ_DEVICE_CONTROL		Winachsf0			IOCTL: 0x2B0034	
61	0.00000391	svchost.exe	IRP_MJ_DEVICE_CONTROL		Winachsf0	SUCCESS	IOCTL: 0x2B0008	
62	0.00000223	svchost.exe	IOCTL_SERIAL_CLEAR_STATS	Winachsf0	SUCCESS		
63	0.00000175	svchost.exe	IOCTL_SERIAL_SET_COMMCONFIG	Winachsf0	SUCCESS		
64	0.00000189	svchost.exe	IOCTL_SERIAL_GET_BAUD_RATE	Winachsf0	SUCCESS		
65	0.00000161	svchost.exe	IOCTL_SERIAL_GET_LINE_CONTROL	Winachsf0	SUCCESS		
66	0.00000140	svchost.exe	IOCTL_SERIAL_GET_CHARS		Winachsf0	SUCCESS		
67	0.00000140	svchost.exe	IOCTL_SERIAL_GET_HANDFLOW	Winachsf0	SUCCESS		
68	0.00000349	svchost.exe	IOCTL_SERIAL_SET_BAUD_RATE	Winachsf0	SUCCESS	Rate: 921600	
69	0.00000223	svchost.exe	IOCTL_SERIAL_SET_DTR		Winachsf0	SUCCESS		
70	0.00000182	svchost.exe	IOCTL_SERIAL_SET_LINE_CONTROL	Winachsf0	SUCCESS	StopBits: 1 Parity: NONE WordLength: 8	
71	0.00000189	svchost.exe	IOCTL_SERIAL_SET_CHAR		Winachsf0	SUCCESS	EOF:0 ERR:0 BRK:0 EVT:0 XON:11 XOFF:13	
72	0.00000175	svchost.exe	IOCTL_SERIAL_SET_HANDFLOW	Winachsf0	SUCCESS	Shake:9 Replace:80 XonLimit:10 XoffLimit:10	
73	0.00000154	svchost.exe	IOCTL_SERIAL_SET_DTR		Winachsf0	SUCCESS		
74	0.00000203	svchost.exe	IOCTL_SERIAL_GET_MODEMSTATUS	Winachsf0	SUCCESS		
75	0.00001543	svchost.exe	IOCTL_SERIAL_SET_WAIT_MASK	Winachsf0	SUCCESS	Mask: 	
76	0.00085744	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 3: AT.	
77	0.00000363	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
78	0.00000370	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
79	0.00000203	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
80	0.01221280	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
81	0.00085625	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 39: AT&FE0V1S0=0&C1&D2+MR=2;+DR=1;+ER=1;W2.	
82	0.00000349	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
83	0.00000412	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
84	0.00000182	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
85	0.01025256	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
86	0.00091555	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 52: ATS7=60S30=0L2M1+ES=3,0,2;+DS=3;+DS44=3;+IFC=2,2;X4.	
87	0.00000223	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
88	0.00000244	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 5: .OK..	
89	0.00000182	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
90	16.87536586	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
91	0.00000377	svchost.exe	IRP_MJ_DEVICE_CONTROL		Winachsf0	SUCCESS	IOCTL: 0x2B0030	
92	0.00089236	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 9: ATDT1311.	
93	0.00000426	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
94	0.00000447	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 27: .+MCR: V92....+MRR: 48000..	
95	0.00000203	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
96	0.64149976	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: .	
97	0.00000391	svchost.exe	IOCTL_SERIAL_GET_COMMSTATUS	Winachsf0	SUCCESS		
98	0.00000440	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 41: .+ER: LAPM....+DR: V44....CONNECT 48000..	
99	0.00000189	svchost.exe	IOCTL_SERIAL_GET_MODEMSTATUS	Winachsf0	SUCCESS		
100	0.00000643	svchost.exe	IRP_MJ_DEVICE_CONTROL		Winachsf0	SUCCESS	IOCTL: 0x2B0008	
101	0.00000775	svchost.exe	IOCTL_SERIAL_SET_WAIT_MASK	Winachsf0	SUCCESS	Mask: RLSD 	
102	0.00000000	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0			
103	0.00000175	svchost.exe	IOCTL_SERIAL_CONFIG_SIZE	Winachsf0	SUCCESS	Size: 96	
104	0.00000161	svchost.exe	IOCTL_SERIAL_GET_COMMCONFIG	Winachsf0	SUCCESS		
105	0.00000140	svchost.exe	IOCTL_SERIAL_GET_BAUD_RATE	Winachsf0	SUCCESS		
106	0.00000161	svchost.exe	IOCTL_SERIAL_GET_LINE_CONTROL	Winachsf0	SUCCESS		
107	0.00000119	svchost.exe	IOCTL_SERIAL_GET_CHARS		Winachsf0	SUCCESS		
108	0.00000140	svchost.exe	IOCTL_SERIAL_GET_HANDFLOW	Winachsf0	SUCCESS		
109	0.00000161	svchost.exe	IOCTL_SERIAL_SET_COMMCONFIG	Winachsf0	SUCCESS		
110	0.00000154	svchost.exe	IOCTL_SERIAL_GET_STATS		Winachsf0	SUCCESS		
111	0.00000405	svchost.exe	IRP_MJ_CREATE			Winachsf0	SUCCESS	Options: Open 	
112	0.00000335	svchost.exe	IOCTL_SERIAL_SET_QUEUE_SIZE	Winachsf0	SUCCESS	InSize: 1514 OutSize: 1514	
113	0.00001138	svchost.exe	IOCTL_SERIAL_PURGE		Winachsf0	SUCCESS	Purge: RXABORT TXCLEAR RXCLEAR	
114	0.00000461	svchost.exe	IOCTL_SERIAL_GET_BAUD_RATE	Winachsf0	SUCCESS		
115	0.00000175	svchost.exe	IOCTL_SERIAL_GET_LINE_CONTROL	Winachsf0	SUCCESS		
116	0.00000154	svchost.exe	IOCTL_SERIAL_GET_CHARS		Winachsf0	SUCCESS		
117	0.00000154	svchost.exe	IOCTL_SERIAL_GET_HANDFLOW	Winachsf0	SUCCESS		
118	0.00000154	svchost.exe	IOCTL_SERIAL_GET_BAUD_RATE	Winachsf0	SUCCESS		
119	0.00000293	svchost.exe	IOCTL_SERIAL_GET_LINE_CONTROL	Winachsf0	SUCCESS		
120	0.00000133	svchost.exe	IOCTL_SERIAL_GET_CHARS		Winachsf0	SUCCESS		
121	0.00000161	svchost.exe	IOCTL_SERIAL_GET_HANDFLOW	Winachsf0	SUCCESS		
122	0.00000377	svchost.exe	IOCTL_SERIAL_SET_BAUD_RATE	Winachsf0	SUCCESS	Rate: 921600	
123	0.00000210	svchost.exe	IOCTL_SERIAL_SET_DTR		Winachsf0	SUCCESS		
124	0.00000175	svchost.exe	IOCTL_SERIAL_SET_LINE_CONTROL	Winachsf0	SUCCESS	StopBits: 1 Parity: NONE WordLength: 8	
125	0.00000217	svchost.exe	IOCTL_SERIAL_SET_CHAR		Winachsf0	SUCCESS	EOF:0 ERR:0 BRK:0 EVT:0 XON:11 XOFF:13	
126	0.00000182	svchost.exe	IOCTL_SERIAL_SET_HANDFLOW	Winachsf0	SUCCESS	Shake:9 Replace:80 XonLimit:10 XoffLimit:10	
127	0.00000168	svchost.exe	IRP_MJ_DEVICE_CONTROL		Winachsf0	INVALID PARAMETER	IOCTL: 0x1B3E80	
128	0.00000147	svchost.exe	IOCTL_SERIAL_SET_QUEUE_SIZE	Winachsf0	SUCCESS	InSize: 4096 OutSize: 4096	
129	0.00000147	svchost.exe	IOCTL_SERIAL_SET_TIMEOUTS	Winachsf0	SUCCESS	RI:-1 RM:0 RC:0 WM:4 WC:4000	
130	0.00000133	svchost.exe	IOCTL_SERIAL_GET_CHARS		Winachsf0	SUCCESS		
131	0.00000161	svchost.exe	IOCTL_SERIAL_SET_CHAR		Winachsf0	SUCCESS	EOF:0 ERR:0 BRK:0 EVT:7e XON:11 XOFF:13	
132	0.00001006	svchost.exe	IOCTL_SERIAL_SET_WAIT_MASK	Winachsf0	SUCCESS	Mask: RXFLAG DSR RLSD ERR RX80FULL 	
133	0.00000391	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 0: 	
134	0.20157562	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
135	0.00066978	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 53: ~.}#.!}!} } }7}"}&} } } } }%%}&}" w}'}'}"}(}"}-}#}&[.~	
136	0.00000426	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
137	0.00002472	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
138	0.00000217	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 69: .}#.!}!.} '}"}&} }*} } }#}$.#}%}&e.3.}'}"}(}"}1}$}%.}3}+}!sgbp	
139	0.00000761	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
140	0.00000196	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
141	0.00001243	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
142	0.00000203	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 22: .}#.!}$} } }'}-}#}&.6~	
143	0.14218029	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
144	0.00024850	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 37: ~.}#.!}$.} }3}1}$}%%.}3}+}!sgbpomank.~	
145	0.00019961	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 47: ~.}#.!}!}!} }4}"}&} } } } }%%}&}" w}'}'}"}(}"..~	
146	0.00000461	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
147	0.00002088	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
148	0.00000203	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 49: .}#.!}!.} }8}"}&} }*} } }#}$.#}%}&e.3.}'}"}(}"..~	
149	0.00781189	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
150	0.00000440	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
151	0.00001983	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
152	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 46: .}#.!}"}!} }4}"}&} } } } }%}&}" w}'}'}"}(}"$.~	
153	0.26224471	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
154	0.00141317	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 50: ~.}#.!}".} }8}"}&} }*} } }#}$.#}%%}&e.3.}'}"}(}"{j~	
155	0.00126175	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 24: ~.!..... w.MSRASV5.20#.~	
156	0.00003143	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 28: ~.!..... w.MSRAS-0-GEORGENv~	
157	0.00001970	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 30: ~.!..... w.....H..@.w.Jb..l.2~	
158	0.00076036	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 26: ~.#.-...USERNAME.PASSWORD..~	
159	0.00000391	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
160	0.00001243	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
161	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 12: ...#.-....#~	
162	0.00000775	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
163	0.00000196	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
164	0.00001131	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
165	0.00000203	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 17: ...!......>...jb~	
166	0.14232989	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
167	0.00002382	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 20: ~.W......<n%%PN..:..~	
168	0.00096807	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 16: ~............9.~	
169	0.00095578	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 34: ~.!.......-....................o.~	
170	0.00002193	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 17: ~.!......>...}].~	
171	0.00000412	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
172	0.00001816	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
173	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 37: .}#.!}(.} }4.W}!}%} }.}!}*<n%PN..:d.~	
174	0.00000768	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
175	0.00000196	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
176	0.00001530	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
177	0.00000196	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 37: .}#.!}(.} }0..}!}&} }*}2}&} } } }!dF~	
178	0.00786755	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
179	0.00000433	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
180	0.00001599	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
181	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 29: ...!.......-................~	
182	0.11096354	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
183	0.00025352	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 16: ~.!..........Z.~	
184	0.00000461	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
185	0.00001369	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
186	0.00000217	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 17: ...!......>.....~	
187	0.11183824	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
188	0.00028041	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 16: ~.!......>...G.~	
189	0.00000447	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
190	0.00001313	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
191	0.00000217	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 17: ...!......>...P.~	
192	4.76940624	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
193	0.00041737	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!F..(......;.>..........."...............F.~	
194	0.00020834	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 335: ~!E..H.....}10.>........D.C.4.$....*.PM....>....................	
195	0.00093999	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!F..(......;,>...........".................~	
196	0.00031994	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!F..(......;+>...........".................~	
197	0.00010832	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 578: ~!E..<.. ..}1.'>..........v..r.<?xml version="1.0" encoding="utf	
198	0.00013200	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 474: ~!E......E.}1.J>.......91ea-af12f0737a59</wsa:MessageID><wsd:App	
199	0.00062592	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!F..(......;)>..........."................L~	
200	0.00047031	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
201	0.00094153	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 168: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
202	0.00056725	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 58: ~!E..4.....}1.)>............ ...............George.......~	
203	0.00011957	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 53: ~!F..0......;.>...........".......................#.~	
204	0.00025255	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 58: ~!E..4.....}1.'>............ ...............George.....H{~	
205	0.00046752	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 578: ~!E..<.. ..}1. >..........v..r.<?xml version="1.0" encoding="utf	
206	0.00076239	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 475: ~!E......E.}1.C>.......91ea-af12f0737a59</wsa:MessageID><wsd:App	
207	0.00039516	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 157: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
208	0.00088300	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 170: ~!E........}1..>..........l..#KM-SEARCH * HTTP/1.1..Host:239.255	
209	0.00072146	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
210	0.00063046	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 335: ~!E..H.....}10.>........D.C.4.$....*.PM....>....................	
211	0.00100097	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
212	0.00075429	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 168: ~!E....}1...}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.25	
213	0.00000419	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
214	0.08778504	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
215	0.00000440	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 585: !E..@|+..4.`.B.[m>.......x'(.A...P.. .z..!........".S..}]&.$.'..	
216	4.08709955	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
217	0.00080785	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 157: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
218	0.00046270	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 171: ~!E....}3...}1..>..........l..#KM-SEARCH * HTTP/1.1..Host:239.25	
219	0.00031771	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
220	0.00063116	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
221	0.00038196	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
222	0.00000377	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
223	0.07201690	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
224	0.00000524	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 519: !E.......5.a..U.}]>....f....2.g...P..(E)......................W<	
225	0.93572996	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
226	0.00000517	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
227	0.07200929	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
228	0.00000524	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 519: !E.......5.a..U.}]>....f....2.g...P..(E)......................W<	
229	0.91991671	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
230	0.00046843	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
231	0.00000475	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
232	0.07227196	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
233	0.00000468	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 519: !E.......5.a..U.}]>....f....2.g...P..(E)......................W<	
234	1.92779501	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
235	0.00000405	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
236	0.07187576	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
237	0.00025499	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 56: ~!E..2.....}1..>....C.....5..!.|............wpad.....D.~	
238	0.00000468	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 519: !E.......5.a..U.}]>....f....2.g...P..(E)......................W<	
239	0.22187094	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
240	0.00000433	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
241	0.00002144	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
242	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 54: !E..2..@.9....C..>....5......|............wpad.....,.~	
243	0.65878540	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
244	0.00071245	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 56: ~!E..2.....}1..>...............>............wpad.....2.~	
245	0.00064282	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 56: ~!E..2.....}1..>...............>............wpad.....MB~	
246	0.00011258	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 167: ~!E........}1..>..........l....M-SEARCH * HTTP/1.1..Host:239.255	
247	0.00066412	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 68: ~!E..>.....}1..>....C...Z.5.*..g............[www.msftncsi.com](www.msftncsi.com)....	
248	0.00000454	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
249	0.00002808	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
250	0.00000217	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 82: !E..N..@.9....C..>....5.Z.:]pg............[www.msftncsi.com](www.msftncsi.com)......	
251	0.04771479	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
252	0.00060098	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 57: ~!E..4..@.....>........J.P.......... .z.................~	
253	0.00000412	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
254	0.07102097	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
255	0.00000461	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 519: !E.......5.a..U.}]>....f....2.g...P..(E)......................W<	
256	0.01586633	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
257	0.00000356	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
258	0.00002060	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
259	0.00000217	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 52: !E..0....;..+....>....P.J0 5.....p...I...........x{~	
260	0.00003227	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!E..(..@....)>........J.P....0 5.P...i....1~	
261	0.18184183	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
262	0.00003303	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 143: ~!E.....@.....>........J.P....0 5.P...}.e..GET /ncsi.txt HTTP/1.	
263	0.00000412	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
264	0.00001942	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
265	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 44: !E..(....;.z7....>....P.J0 7X...KP...o.....~	
266	0.00017649	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!E..(. @....'>........J.P...K0 5.P...i....(~	
267	0.00001013	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
268	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
269	0.06419419	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
270	0.00000447	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 435: !E.......;.x.....>....P.J0 5....KP.......HTTP/1.1 200 OK..Cache-	
271	0.00003345	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!E..(.!@....&>........J.P...K0 7YP...ha..6.~	
272	0.66556811	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
273	0.00006775	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!E..(."@....%%>........J.P...K0 7YP...o.....~	
274	0.00000370	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
275	0.07953469	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
276	0.00000475	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 519: !E.......5.a..U.}]>....f....2.g...P..(E)......................W<	
277	0.43590652	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
278	0.00190576	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 57: ~!E..4.#@...tb>....U.].K.P.......... .<@................~	
279	0.00000391	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
280	0.00002123	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
281	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 52: !E..0.n..;.5..U.]>....P.K..zl....p....H............~	
282	0.00003157	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 45: ~!E..(.$@...tm>....U.].K.P......zmP....p....~	
283	0.27771567	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
284	0.00088251	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 581: ~!E..@.%%@...rT>....U.].K.P......zmP...C)..GET /safebrowsing/upd	
285	0.00089271	svchost.exe	IRP_MJ_WRITE			Winachsf0	SUCCESS	Length 75: ~!E..F.&@...tM>....U.].K.P......zmP.......SbDZzrULczgx68ETdQT97K	
286	0.00000398	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 1: ~	
287	0.00001977	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0	SUCCESS		
288	0.00000210	svchost.exe	IRP_MJ_READ				Winachsf0	SUCCESS	Length 44: !E..(....;....U.]>....P.K..zm... P....;...W~	
289	0.00000000	svchost.exe	IOCTL_SERIAL_WAIT_ON_MASK	Winachsf0

The interesting part starts from 133 to 192...

---

