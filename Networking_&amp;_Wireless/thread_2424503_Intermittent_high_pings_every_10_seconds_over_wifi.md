---
title: "Intermittent high pings every 10 seconds over wifi (USB Adapter TP-Link T9UH V2)"
date: 2019-08-09
forum: Networking &amp; Wireless
---

### Post by btetvu on 2019-08-09
Hello all,

I'm at the end of my patience here with my wi-fi. Been  busy for days trying to sort out different things but I cannot get a  decent ping to my own router whatsoever.
Hope you can help me out.

Some more info you need:
- 5Ghz network (not hidden), free channel, used Wi-Fi Analyzer to detect a good channel
- Live in an appartment with many networks though
- Using the TP-Link T9UH V2
- Installed the correct driver
> rtl8814au, 4.3.21, 5.0.0-23-generic, x86_64: installed
- Using Pop!_OS (uname -a)
> Linux random 5.0.0-23-generic #24-Ubuntu SMP Mon Jul 29 15:36:44 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

The problem is this, I should be around 3-4ms all the time when I ping to my router:
```

64 bytes from 192.168.1.1: icmp_seq=6186 ttl=64 time=8.09 ms
64 bytes from 192.168.1.1: icmp_seq=6187 ttl=64 time=36.2 ms
64 bytes from 192.168.1.1: icmp_seq=6188 ttl=64 time=23.9 ms
64 bytes from 192.168.1.1: icmp_seq=6189 ttl=64 time=13.1 ms
64 bytes from 192.168.1.1: icmp_seq=6190 ttl=64 time=3687 ms
64 bytes from 192.168.1.1: icmp_seq=6191 ttl=64 time=2672 ms
64 bytes from 192.168.1.1: icmp_seq=6192 ttl=64 time=1652 ms
64 bytes from 192.168.1.1: icmp_seq=6193 ttl=64 time=628 ms
64 bytes from 192.168.1.1: icmp_seq=6194 ttl=64 time=48.8 ms
64 bytes from 192.168.1.1: icmp_seq=6195 ttl=64 time=5.14 ms
64 bytes from 192.168.1.1: icmp_seq=6196 ttl=64 time=54.6 ms
64 bytes from 192.168.1.1: icmp_seq=6197 ttl=64 time=4.39 ms
64 bytes from 192.168.1.1: icmp_seq=6198 ttl=64 time=97.6 ms
64 bytes from 192.168.1.1: icmp_seq=6199 ttl=64 time=102 ms
64 bytes from 192.168.1.1: icmp_seq=6200 ttl=64 time=5.60 ms
64 bytes from 192.168.1.1: icmp_seq=6201 ttl=64 time=4.02 ms
64 bytes from 192.168.1.1: icmp_seq=6202 ttl=64 time=6.58 ms
64 bytes from 192.168.1.1: icmp_seq=6203 ttl=64 time=60.4 ms
64 bytes from 192.168.1.1: icmp_seq=6204 ttl=64 time=623 ms
64 bytes from 192.168.1.1: icmp_seq=6205 ttl=64 time=3650 ms
64 bytes from 192.168.1.1: icmp_seq=6206 ttl=64 time=2630 ms
64 bytes from 192.168.1.1: icmp_seq=6207 ttl=64 time=1606 ms
64 bytes from 192.168.1.1: icmp_seq=6208 ttl=64 time=582 ms
64 bytes from 192.168.1.1: icmp_seq=6209 ttl=64 time=38.1 ms
64 bytes from 192.168.1.1: icmp_seq=6210 ttl=64 time=76.6 ms
64 bytes from 192.168.1.1: icmp_seq=6211 ttl=64 time=3.97 ms
64 bytes from 192.168.1.1: icmp_seq=6212 ttl=64 time=44.6 ms
64 bytes from 192.168.1.1: icmp_seq=6213 ttl=64 time=4.49 ms
64 bytes from 192.168.1.1: icmp_seq=6214 ttl=64 time=217 ms
64 bytes from 192.168.1.1: icmp_seq=6215 ttl=64 time=19.5 ms
64 bytes from 192.168.1.1: icmp_seq=6216 ttl=64 time=42.10 ms
64 bytes from 192.168.1.1: icmp_seq=6217 ttl=64 time=20.5 ms
64 bytes from 192.168.1.1: icmp_seq=6218 ttl=64 time=44.4 ms
64 bytes from 192.168.1.1: icmp_seq=6219 ttl=64 time=4.71 ms
64 bytes from 192.168.1.1: icmp_seq=6220 ttl=64 time=5.55 ms
64 bytes from 192.168.1.1: icmp_seq=6221 ttl=64 time=119 ms
64 bytes from 192.168.1.1: icmp_seq=6222 ttl=64 time=7.13 ms
64 bytes from 192.168.1.1: icmp_seq=6223 ttl=64 time=3.92 ms
64 bytes from 192.168.1.1: icmp_seq=6224 ttl=64 time=12.3 ms
64 bytes from 192.168.1.1: icmp_seq=6225 ttl=64 time=3.96 ms
64 bytes from 192.168.1.1: icmp_seq=6226 ttl=64 time=11.0 ms
64 bytes from 192.168.1.1: icmp_seq=6227 ttl=64 time=5.06 ms
64 bytes from 192.168.1.1: icmp_seq=6228 ttl=64 time=38.4 ms
64 bytes from 192.168.1.1: icmp_seq=6229 ttl=64 time=253 ms
64 bytes from 192.168.1.1: icmp_seq=6230 ttl=64 time=105 ms
64 bytes from 192.168.1.1: icmp_seq=6231 ttl=64 time=3.97 ms
64 bytes from 192.168.1.1: icmp_seq=6232 ttl=64 time=5.14 ms
64 bytes from 192.168.1.1: icmp_seq=6233 ttl=64 time=5.89 ms
64 bytes from 192.168.1.1: icmp_seq=6234 ttl=64 time=5.57 ms
64 bytes from 192.168.1.1: icmp_seq=6235 ttl=64 time=3527 ms
64 bytes from 192.168.1.1: icmp_seq=6236 ttl=64 time=2500 ms
64 bytes from 192.168.1.1: icmp_seq=6237 ttl=64 time=1476 ms
64 bytes from 192.168.1.1: icmp_seq=6238 ttl=64 time=452 ms
64 bytes from 192.168.1.1: icmp_seq=6239 ttl=64 time=3.98 ms
64 bytes from 192.168.1.1: icmp_seq=6240 ttl=64 time=4.01 ms
64 bytes from 192.168.1.1: icmp_seq=6241 ttl=64 time=3.88 ms
64 bytes from 192.168.1.1: icmp_seq=6242 ttl=64 time=3.81 ms
64 bytes from 192.168.1.1: icmp_seq=6243 ttl=64 time=3.89 ms
64 bytes from 192.168.1.1: icmp_seq=6244 ttl=64 time=4.62 ms
64 bytes from 192.168.1.1: icmp_seq=6245 ttl=64 time=4.07 ms
64 bytes from 192.168.1.1: icmp_seq=6246 ttl=64 time=4.94 ms
64 bytes from 192.168.1.1: icmp_seq=6247 ttl=64 time=4.44 ms
64 bytes from 192.168.1.1: icmp_seq=6248 ttl=64 time=235 ms
64 bytes from 192.168.1.1: icmp_seq=6249 ttl=64 time=4.97 ms
64 bytes from 192.168.1.1: icmp_seq=6250 ttl=64 time=3457 ms
64 bytes from 192.168.1.1: icmp_seq=6251 ttl=64 time=2449 ms
64 bytes from 192.168.1.1: icmp_seq=6252 ttl=64 time=1425 ms
64 bytes from 192.168.1.1: icmp_seq=6253 ttl=64 time=401 ms
64 bytes from 192.168.1.1: icmp_seq=6254 ttl=64 time=135 ms
64 bytes from 192.168.1.1: icmp_seq=6255 ttl=64 time=15.3 ms
64 bytes from 192.168.1.1: icmp_seq=6256 ttl=64 time=3.87 ms
64 bytes from 192.168.1.1: icmp_seq=6257 ttl=64 time=20.8 ms
64 bytes from 192.168.1.1: icmp_seq=6258 ttl=64 time=5.04 ms
64 bytes from 192.168.1.1: icmp_seq=6259 ttl=64 time=37.6 ms
64 bytes from 192.168.1.1: icmp_seq=6260 ttl=64 time=4.11 ms
64 bytes from 192.168.1.1: icmp_seq=6261 ttl=64 time=58.9 ms
64 bytes from 192.168.1.1: icmp_seq=6262 ttl=64 time=7.72 ms
64 bytes from 192.168.1.1: icmp_seq=6263 ttl=64 time=51.2 ms
64 bytes from 192.168.1.1: icmp_seq=6264 ttl=64 time=140 ms
64 bytes from 192.168.1.1: icmp_seq=6265 ttl=64 time=3360 ms
64 bytes from 192.168.1.1: icmp_seq=6266 ttl=64 time=2354 ms
64 bytes from 192.168.1.1: icmp_seq=6267 ttl=64 time=1330 ms
64 bytes from 192.168.1.1: icmp_seq=6268 ttl=64 time=308 ms
64 bytes from 192.168.1.1: icmp_seq=6269 ttl=64 time=35.8 ms
64 bytes from 192.168.1.1: icmp_seq=6270 ttl=64 time=10.6 ms
64 bytes from 192.168.1.1: icmp_seq=6271 ttl=64 time=21.7 ms
64 bytes from 192.168.1.1: icmp_seq=6272 ttl=64 time=59.8 ms
64 bytes from 192.168.1.1: icmp_seq=6273 ttl=64 time=5.43 ms
64 bytes from 192.168.1.1: icmp_seq=6274 ttl=64 time=16.1 ms
64 bytes from 192.168.1.1: icmp_seq=6275 ttl=64 time=106 ms
64 bytes from 192.168.1.1: icmp_seq=6276 ttl=64 time=5.01 ms
64 bytes from 192.168.1.1: icmp_seq=6277 ttl=64 time=14.4 ms
64 bytes from 192.168.1.1: icmp_seq=6278 ttl=64 time=17.4 ms
64 bytes from 192.168.1.1: icmp_seq=6279 ttl=64 time=17.6 ms
64 bytes from 192.168.1.1: icmp_seq=6280 ttl=64 time=3303 ms
64 bytes from 192.168.1.1: icmp_seq=6281 ttl=64 time=2297 ms
64 bytes from 192.168.1.1: icmp_seq=6282 ttl=64 time=1273 ms
64 bytes from 192.168.1.1: icmp_seq=6283 ttl=64 time=251 ms
64 bytes from 192.168.1.1: icmp_seq=6284 ttl=64 time=23.1 ms
64 bytes from 192.168.1.1: icmp_seq=6285 ttl=64 time=42.8 ms
64 bytes from 192.168.1.1: icmp_seq=6286 ttl=64 time=30.4 ms
64 bytes from 192.168.1.1: icmp_seq=6287 ttl=64 time=4.29 ms
64 bytes from 192.168.1.1: icmp_seq=6288 ttl=64 time=46.4 ms
64 bytes from 192.168.1.1: icmp_seq=6289 ttl=64 time=4.03 ms
64 bytes from 192.168.1.1: icmp_seq=6290 ttl=64 time=56.9 ms
64 bytes from 192.168.1.1: icmp_seq=6291 ttl=64 time=4.85 ms
64 bytes from 192.168.1.1: icmp_seq=6292 ttl=64 time=4.97 ms
64 bytes from 192.168.1.1: icmp_seq=6293 ttl=64 time=16.2 ms
64 bytes from 192.168.1.1: icmp_seq=6294 ttl=64 time=187 ms
64 bytes from 192.168.1.1: icmp_seq=6295 ttl=64 time=3208 ms
64 bytes from 192.168.1.1: icmp_seq=6296 ttl=64 time=2202 ms
64 bytes from 192.168.1.1: icmp_seq=6297 ttl=64 time=1178 ms
64 bytes from 192.168.1.1: icmp_seq=6298 ttl=64 time=154 ms
64 bytes from 192.168.1.1: icmp_seq=6299 ttl=64 time=3.96 ms
64 bytes from 192.168.1.1: icmp_seq=6300 ttl=64 time=3.97 ms
64 bytes from 192.168.1.1: icmp_seq=6301 ttl=64 time=3.95 ms
64 bytes from 192.168.1.1: icmp_seq=6302 ttl=64 time=3.89 ms
64 bytes from 192.168.1.1: icmp_seq=6303 ttl=64 time=3.87 ms
64 bytes from 192.168.1.1: icmp_seq=6304 ttl=64 time=3.90 ms
64 bytes from 192.168.1.1: icmp_seq=6305 ttl=64 time=3.94 ms
64 bytes from 192.168.1.1: icmp_seq=6306 ttl=64 time=152 ms
64 bytes from 192.168.1.1: icmp_seq=6307 ttl=64 time=36.4 ms
64 bytes from 192.168.1.1: icmp_seq=6308 ttl=64 time=11.9 ms
64 bytes from 192.168.1.1: icmp_seq=6309 ttl=64 time=4.67 ms
64 bytes from 192.168.1.1: icmp_seq=6310 ttl=64 time=3161 ms
64 bytes from 192.168.1.1: icmp_seq=6311 ttl=64 time=2154 ms
64 bytes from 192.168.1.1: icmp_seq=6312 ttl=64 time=1129 ms
64 bytes from 192.168.1.1: icmp_seq=6313 ttl=64 time=105 ms
64 bytes from 192.168.1.1: icmp_seq=6314 ttl=64 time=95.5 ms
64 bytes from 192.168.1.1: icmp_seq=6315 ttl=64 time=230 ms
64 bytes from 192.168.1.1: icmp_seq=6316 ttl=64 time=24.7 ms
64 bytes from 192.168.1.1: icmp_seq=6317 ttl=64 time=4.89 ms
64 bytes from 192.168.1.1: icmp_seq=6318 ttl=64 time=21.7 ms
64 bytes from 192.168.1.1: icmp_seq=6319 ttl=64 time=22.5 ms
64 bytes from 192.168.1.1: icmp_seq=6320 ttl=64 time=46.4 ms
64 bytes from 192.168.1.1: icmp_seq=6321 ttl=64 time=24.8 ms
64 bytes from 192.168.1.1: icmp_seq=6322 ttl=64 time=30.5 ms
64 bytes from 192.168.1.1: icmp_seq=6323 ttl=64 time=3.92 ms
64 bytes from 192.168.1.1: icmp_seq=6324 ttl=64 time=55.8 ms
64 bytes from 192.168.1.1: icmp_seq=6325 ttl=64 time=3083 ms
64 bytes from 192.168.1.1: icmp_seq=6326 ttl=64 time=2077 ms
64 bytes from 192.168.1.1: icmp_seq=6327 ttl=64 time=1053 ms
64 bytes from 192.168.1.1: icmp_seq=6328 ttl=64 time=28.7 ms
64 bytes from 192.168.1.1: icmp_seq=6329 ttl=64 time=10.8 ms
64 bytes from 192.168.1.1: icmp_seq=6330 ttl=64 time=4.94 ms
64 bytes from 192.168.1.1: icmp_seq=6331 ttl=64 time=5.39 ms
64 bytes from 192.168.1.1: icmp_seq=6332 ttl=64 time=10.1 ms
64 bytes from 192.168.1.1: icmp_seq=6333 ttl=64 time=26.4 ms
64 bytes from 192.168.1.1: icmp_seq=6334 ttl=64 time=3.90 ms
64 bytes from 192.168.1.1: icmp_seq=6335 ttl=64 time=22.2 ms
64 bytes from 192.168.1.1: icmp_seq=6336 ttl=64 time=13.2 ms
64 bytes from 192.168.1.1: icmp_seq=6337 ttl=64 time=22.2 ms
64 bytes from 192.168.1.1: icmp_seq=6338 ttl=64 time=118 ms
64 bytes from 192.168.1.1: icmp_seq=6339 ttl=64 time=30.2 ms
64 bytes from 192.168.1.1: icmp_seq=6340 ttl=64 time=22.7 ms
64 bytes from 192.168.1.1: icmp_seq=6341 ttl=64 time=34.3 ms
64 bytes from 192.168.1.1: icmp_seq=6342 ttl=64 time=4.05 ms
64 bytes from 192.168.1.1: icmp_seq=6343 ttl=64 time=7.37 ms
64 bytes from 192.168.1.1: icmp_seq=6344 ttl=64 time=5.93 ms
64 bytes from 192.168.1.1: icmp_seq=6345 ttl=64 time=3.97 ms
64 bytes from 192.168.1.1: icmp_seq=6346 ttl=64 time=30.3 ms
64 bytes from 192.168.1.1: icmp_seq=6347 ttl=64 time=14.1 ms
64 bytes from 192.168.1.1: icmp_seq=6348 ttl=64 time=5.29 ms
64 bytes from 192.168.1.1: icmp_seq=6349 ttl=64 time=4.79 ms
64 bytes from 192.168.1.1: icmp_seq=6350 ttl=64 time=4.16 ms
64 bytes from 192.168.1.1: icmp_seq=6351 ttl=64 time=4.02 ms
64 bytes from 192.168.1.1: icmp_seq=6352 ttl=64 time=13.4 ms
64 bytes from 192.168.1.1: icmp_seq=6353 ttl=64 time=6.95 ms
64 bytes from 192.168.1.1: icmp_seq=6354 ttl=64 time=9.81 ms
64 bytes from 192.168.1.1: icmp_seq=6355 ttl=64 time=2971 ms
64 bytes from 192.168.1.1: icmp_seq=6356 ttl=64 time=1944 ms
64 bytes from 192.168.1.1: icmp_seq=6357 ttl=64 time=952 ms
64 bytes from 192.168.1.1: icmp_seq=6358 ttl=64 time=150 ms
64 bytes from 192.168.1.1: icmp_seq=6359 ttl=64 time=688 ms
64 bytes from 192.168.1.1: icmp_seq=6360 ttl=64 time=18.8 ms
64 bytes from 192.168.1.1: icmp_seq=6361 ttl=64 time=4.07 ms
64 bytes from 192.168.1.1: icmp_seq=6362 ttl=64 time=3.92 ms
64 bytes from 192.168.1.1: icmp_seq=6363 ttl=64 time=3.90 ms
64 bytes from 192.168.1.1: icmp_seq=6364 ttl=64 time=3.84 ms
64 bytes from 192.168.1.1: icmp_seq=6365 ttl=64 time=3.92 ms
64 bytes from 192.168.1.1: icmp_seq=6366 ttl=64 time=3.93 ms
64 bytes from 192.168.1.1: icmp_seq=6367 ttl=64 time=3.89 ms
64 bytes from 192.168.1.1: icmp_seq=6368 ttl=64 time=3.89 ms
64 bytes from 192.168.1.1: icmp_seq=6369 ttl=64 time=52.2 ms
64 bytes from 192.168.1.1: icmp_seq=6370 ttl=64 time=2934 ms
64 bytes from 192.168.1.1: icmp_seq=6371 ttl=64 time=1904 ms
64 bytes from 192.168.1.1: icmp_seq=6372 ttl=64 time=880 ms
64 bytes from 192.168.1.1: icmp_seq=6373 ttl=64 time=21.5 ms
64 bytes from 192.168.1.1: icmp_seq=6374 ttl=64 time=10.9 ms
64 bytes from 192.168.1.1: icmp_seq=6375 ttl=64 time=4.35 ms

```

Here is the file that was requested in the sticky:
[HTML]https://paste.ubuntu.com/p/5BBbcXKyCy/[/HTML]
Clickable link: [https://paste.ubuntu.com/p/5BBbcXKyCy/](https://paste.ubuntu.com/p/5BBbcXKyCy/)

I hope some with more knowledge than me can help me out here. I sadly have no option to get a wire.
Thanks in advance!

Kind regards

---

