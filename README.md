# Asynchronous FIFO using Verilog
The name FIFO stands for First In First Out, meaning that the data written first serially into the buffer, will be read out from the buffer first. It mainly consists of a set of a read and write pointer, and `FIFO` array for storage control signals. Storage may be static random access memory (SRAM), flip-flops, latches or any other suitable form of storage. For FIFOs of non-trivial size, a dual-port SRAM is usually used, where one port is dedicated to writing and the other to reading.

#When use FIFO FIFOs are often used to safely pass data from one clock domain to another asynchronous clock domain. FIFO can also used between different date width.

To address the metastability issues, we convert the read and write pointers to their corresponding gray ccode values that ensures only one bit is flipped with each clock transition.

The files `fifo.v` and `sync_fifo_tb.v` simulate a synchronous FIFO, that works on a single clock cycle as both the read and write cycles. 

The two clock signals given to the module are `wr_clk` and `rd_clk`. The many variables used in the module are:
 Markup : 1. `readEn` is read enable signal, which enables the buffer to read the stored data.
2. `writeEn` is the write enable signal, which enables the buffer to get some data written in it.
3. `buf_in` is the data that will be written into the buffer.
4. `buf_out` is the data that is stored in the buffer and will be read out from it.
5. `Full` and `Empty` are a flags that indicate when the buffer gets full, and no more data can be written or that the buffer is empty and no more data can be read.
6. `rd_ptr` is the read pointer, which increments as something is read from the buffer.
7. `wr_ptr` is the write pointer, which increments as some data is written into the buffer.
8. `rd_ptr_g` and `wr_ptr_g` are both gray-converted values of the read and write pointers respectively.
