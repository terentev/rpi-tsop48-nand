It might be compiled on Raspberry Pi by command like
g++ rpi-raw-nand-v3.c -o rpi-raw-nand-v3

I tested on MX30LF2G18AC + rpi 4

Whats work?
1) read

  ./rpi-raw-nand-v3 25 read_full 0 131072 read-full-file
  
2) write after erase

rpi-raw-nand-v3 100 erase_blocks 0 2048
for i in {0..131071}; do sleep 0.01 ; ./rpi-raw-nand-v3 100 write_full $i 1 read-full-file; done

to view page XXX

./rpi-raw-nand-v3 25 read_full XXX 1 out-file; xxd out-file
