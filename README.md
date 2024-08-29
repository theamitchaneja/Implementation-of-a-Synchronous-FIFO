/// LOGIC FOR Synchronous FIFO Design ///

Initialization:

Input: clk, rst_n, w_en, r_en, data_in (16 bits)

Output: data_out (16 bits), full, empty

Internal registers: w_ptr, r_ptr (4 bits each), FIFO array (8x16 bits)


Reset Logic:

On the positive edge of clk or negative edge of rst_n:

If rst_n is low:

Set data_out to 0
Set w_ptr to 0
Set r_ptr to 0


Write Logic:

On the positive edge of clk:

If full is false and w_en is true:

Write data_in to FIFO at the location indicated by w_ptr[2:0]

Increment w_ptr by 1


Read Logic:

On the positive edge of clk:

If empty is false and r_en is true:

Read data from FIFO at the location indicated by r_ptr[2:0] and assign it to data_out

Increment r_ptr by 1


Status Flags:

empty is true if w_ptr equals r_ptr

full is true if the MSB of w_ptr is not equal to the MSB of r_ptr and the lower bits of w_ptr are equal to the lower bits of r_ptr
