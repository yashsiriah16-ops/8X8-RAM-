# 8X8-RAM-

module eightintoeightRAM(
    input clk,
    input rst,
    input wr_enb,
    input rd_enb,
    input [3:0] wr_addr,
    input [3:0] rd_addr,
    input [7:0] data_in,
    output reg [7:0] data_out
);

   reg [7:0] mem [7:0];
    integer i;

   always @(posedge clk or posedge rst) begin
        if (rst) begin
            for (i = 0; i < 8; i = i + 1)
                mem[i] <= 8'b0;
            data_out <= 8'b0;
        end
        else begin
            if (wr_enb)
                mem[wr_addr] <= data_in;
            if (rd_enb)
                data_out <= mem[rd_addr];
        end
    end
endmodule
