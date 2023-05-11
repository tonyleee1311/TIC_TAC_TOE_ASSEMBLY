.text
main:
#s0 hold address of array line1
#s1 hold address of array line2
#s2 hold address of array line3
#s3 hold address of array line4
#s4 hold address of array line5
addi $s6, $zero, 2 #use for undo, if undo is call, $s6=0, for player 1
addi $s7, $zero, 2 #use for undo, if undo is callm $s7=0, for player 2
jal game_instruction
jal init_game
jal print_tic_tac_toe
jal start_the_game

end:

li $v0, 10                  # exit
syscall
#end of main, below is defined function
init_game:
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
	addi $t0, $zero, 45
	addi $t1, $zero, 0
init_here:
	beq $t1, 5, exit
	sb $t0, 0($s0)
	sb $t0, 0($s1)
	sb $t0, 0($s2)
	sb $t0, 0($s3)
	sb $t0, 0($s4)
	addi $t1, $t1, 1
	addi $s0, $s0, 1
	addi $s1, $s1, 1
	addi $s2, $s2, 1
	addi $s3, $s3, 1
	addi $s4, $s4, 1
	j init_here
exit:
	jr $ra

game_instruction:
	li $v0, 4
	la $a0, instruction
	syscall
	li $v0, 4
	la $a0, first_rule
	syscall
	li $v0, 4
	la $a0, second_rule
	syscall
	li $v0, 4
	la $a0, example_input
	syscall
	li $v0, 4
	la $a0, third_rule
	syscall
	li $v0, 4
	la $a0, fourth_rule
	syscall
	li $v0, 4
	la $a0, last_rule
	syscall
	li $v0, 4
	la $a0, board_display
	syscall
	jr $ra

print_tic_tac_toe:
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
	
#The index of column
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $t1, $zero, 0
create_0:
	beq $t1, 5, exit0
	add $a0, $t1, $0
	li $v0, 1
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $t1, $t1, 1
	j create_0
	exit0:	
# new line
	li, $v0, 4
	la $a0, newline
	syscall
#first line 
	li $v0, 4
	la $a0, space
	syscall
	addi $a0, $zero, 0
	li $v0, 1
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $t1, $zero, 0
create_1:
	beq $t1, 5, exit1
	lb $t0, 0($s0)
	move $a0, $t0
	li $v0, 11
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $s0, $s0, 1
	addi $t1, $t1, 1
	j create_1
	exit1:
# new line
	li, $v0, 4
	la $a0, newline
	syscall
#print the second line
	li $v0, 4
	la $a0, space
	syscall
	addi $a0, $zero, 1
	li $v0, 1
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $t1, $zero, 0
create_2:
	beq $t1, 5, exit2
	lb $t0, 0($s1)
	move $a0, $t0
	li $v0, 11
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $s1, $s1, 1
	addi $t1, $t1, 1
	j create_2
exit2:
# new line
	li, $v0, 4
	la $a0, newline
	syscall
#print the third line
	li $v0, 4
	la $a0, space
	syscall
	addi $a0, $zero, 2
	li $v0, 1
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $t1, $zero, 0
create_3:
	beq $t1, 5, exit3
	lb $t0, 0($s2)
	move $a0, $t0
	li $v0, 11
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $s2, $s2, 1
	addi $t1, $t1, 1
	j create_3
exit3:
# new line
	li, $v0, 4
	la $a0, newline
	syscall
#print the fourth line
	li $v0, 4
	la $a0, space
	syscall
	addi $a0, $zero, 3
	li $v0, 1
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $t1, $zero, 0
create_4:
	beq $t1, 5, exit4
	lb $t0, 0($s3)
	move $a0, $t0
	li $v0, 11
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $s3, $s3, 1
	addi $t1, $t1, 1
	j create_4
exit4:
# new line
	li, $v0, 4
	la $a0, newline
	syscall
#print the fifth line
	li $v0, 4
	la $a0, space
	syscall
	addi $a0, $zero, 4
	li $v0, 1
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $t1, $zero, 0
create_5:
	beq $t1, 5, exit5
	lb $t0, 0($s4)
	move $a0, $t0
	li $v0, 11
	syscall
	li $v0, 4
	la $a0, space
	syscall
	li $v0, 4
	la $a0, space
	syscall
	addi $s4, $s4, 1
	addi $t1, $t1, 1
	j create_5
	exit5:
# new line
	li, $v0, 4
	la $a0, newline
	syscall
# new line
	li, $v0, 4
	la $a0, newline
	syscall
	jr $ra

#start the game function
start_the_game:
#Don't need to return in this function.
#1st turn
	play1_input_again_1:
	jal play1_input
	jal check_middle_point
	jal print_tic_tac_toe
	#undo for player 1
	#if $s6=0, run out of opportunities to undo.
	beq $s6, 0, continue_to_play_x1
	jal Undo_play1
	#$s5=1, implement undo fuction, otherwise no.
	beq $s5, 1, play1_input_again_1
	continue_to_play_x1:
	play2_input_again_1:
	jal play2_input
	jal check_middle_point
	jal print_tic_tac_toe
	#undo for player 2
	#if $s7=0, run out of opportunities to undo
	beq $s7, 0, continue_to_play_y1
	jal Undo_play2
	#$s5=1, implement undo fuction, otherwise no.
	beq $s5, 1, play2_input_again_1 
	continue_to_play_y1:
#2rd turn to 12th turn
	add $a3, $zero, $zero
	keep_input_data:
	beq $a3, 11, stop_input
	play1_input_again_2to11:
	jal play1_input
	jal print_tic_tac_toe
	jal win_condition
	#undo for player 1
	#if $s6=0, run out of opportunities to undo
	beq $s6, 0, continue_to_play_x2to11
	jal Undo_play1
	#$s5=1, implement undo fuction, otherwise no.
	beq $s5, 1, play1_input_again_2to11
	continue_to_play_x2to11:
	play2_input_again_2to11:
	jal play2_input
	jal print_tic_tac_toe
	jal win_condition
	#undo for player 2
	#if $s7=0, run out of opportunities to undo
	beq $s7, 0, continue_to_play_y2to11
	jal Undo_play2
	#$s5=1, implement undo fuction, otherwise no.
	beq $s5, 1, play2_input_again_2to11
	continue_to_play_y2to11:
	addi $a3, $a3, 1
	j keep_input_data
	stop_input:
#Last turn: 
	jal play1_input
	jal print_tic_tac_toe
	jal win_condition
	j draw_game
#end of start the game function

#play1_input function	
play1_input:
#a1 store the value of row, a2 store the value of column
#call another function in this function
	addi $sp, $sp, -4
	sw $ra, 0($sp)
input_again_1:
	# new line
	li, $v0, 4
	la $a0, newline
	syscall
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
	li, $v0, 4
	la $a0, player1_input_row
	syscall
	li $v0, 5
	syscall
	add $a1, $0, $v0
	li, $v0, 4
	la $a0, player1_input_column
	syscall
	li $v0, 5
	syscall
	add $a2, $0, $v0
#check out of range
	jal check_valid 
#check first line
	beq $a1,0,store_datax1
	j exit_store_x1
	store_datax1:
	add $s0, $s0, $a2
	addi $t0, $zero, 88 #store 'X'
#check if the position is already marked or not
	lb $t2, 0($s0)
	jal already_marked_1
	sb $t0, 0($s0)	#store 'X' to the board
	j finish_storing_x
	exit_store_x1:
#check second line
	beq $a1,1,store_datax2
	j exit_store_x2
	store_datax2:
	add $s1, $s1, $a2
	addi $t0, $zero, 88 #store 'X'
#check if the position is already marked or not
	lb $t2, 0($s1)
	jal already_marked_1
	sb $t0, 0($s1)	#store 'X' to the board
	j finish_storing_x
	exit_store_x2:
#check third line
	beq $a1,2,store_datax3
	j exit_store_x3
	store_datax3:
	add $s2, $s2, $a2
	addi $t0, $zero, 88 #store 'X'
#check if the position is already marked or not
	lb $t2, 0($s2)
	jal already_marked_1
	sb $t0, 0($s2)	#store 'X' to the board
	j finish_storing_x
	exit_store_x3:
#check fourth line
	beq $a1,3,store_datax4
	j exit_store_x4
	store_datax4:
	add $s3, $s3, $a2
	addi $t0, $zero, 88 #store 'X'
#check if the position is already marked or not
	lb $t2, 0($s3)
	jal already_marked_1
	sb $t0, 0($s3)	#store 'X' to the board
	j finish_storing_x
	exit_store_x4:
#check fifth line
	beq $a1,4,store_datax5
	j exit_store_x5
	store_datax5:
	add $s4, $s4, $a2
	addi $t0, $zero, 88 #store 'X'
#check if the position is already marked or not
	lb $t2, 0($s4)
	jal already_marked_1
	sb $t0, 0($s4)	#store 'X' to the board
	j finish_storing_x
	exit_store_x5:
	finish_storing_x:
	# new line
	li, $v0, 4
	la $a0, newline
	syscall
	lw $ra, 0($sp)
	addi $sp, $sp, 4
	jr $ra
	
#end of play1_input function	
	
#play2_input function
play2_input:
#call another function in this function
	addi $sp, $sp, -4
	sw $ra, 0($sp)
#a1 store the value of row, a2 store the value of column
input_again_2:
	# new line
	li, $v0, 4
	la $a0, newline
	syscall
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
	li, $v0, 4
	la $a0, player2_input_row
	syscall
	li $v0, 5
	syscall
	add $a1, $0, $v0
	li, $v0, 4
	la $a0, player2_input_column
	syscall
	li $v0, 5
	syscall
	add $a2, $0, $v0
#check out of range
	jal check_valid
#check first line
	beq $a1,0,store_datay1
	j exit_store_y1
	store_datay1:
	add $s0, $s0, $a2
	addi $t0, $zero, 79 #store 'O'
#check if the position is already marked or not
	lb $t2, 0($s0)
	jal already_marked_2
	sb $t0, 0($s0) #store 'O' to the board
	j finish_storing_y
	exit_store_y1:
#check second line
	beq $a1,1,store_datay2
	j exit_store_y2
	store_datay2:
	add $s1, $s1, $a2
	addi $t0, $zero, 79 #store 'O'
#check if the position is already marked or not
	lb $t2, 0($s1)
	jal already_marked_2
	sb $t0, 0($s1)	#store 'O' to the board
	j finish_storing_y
	exit_store_y2:
#check third line
	beq $a1,2,store_datay3
	j exit_store_y3
	store_datay3:
	add $s2, $s2, $a2
	addi $t0, $zero, 79 #store 'O'
#check if the position is already marked or not
	lb $t2, 0($s2)
	jal already_marked_2
	sb $t0, 0($s2)	#store 'O' to the board
	j finish_storing_y
	exit_store_y3:
#check fourth line
	beq $a1,3,store_datay4
	j exit_store_y4
	store_datay4:
	add $s3, $s3, $a2
	addi $t0, $zero, 79 #store 'O'
#check if the position is already marked or not
	lb $t2, 0($s3)
	jal already_marked_2
	sb $t0, 0($s3)	#store 'O' to the board
	j finish_storing_y
	exit_store_y4:
#check fifth line
	beq $a1,4,store_datay5
	j exit_store_y5
	store_datay5:
	add $s4, $s4, $a2
	addi $t0, $zero, 79 #store 'O'
#check if the position is already marked or not
	lb $t2, 0($s4)
	jal already_marked_2
	sb $t0, 0($s4)	#store 'O' to the board
	j finish_storing_y
	exit_store_y5:
	finish_storing_y:
	# new line
	li, $v0, 4
	la $a0, newline
	syscall
	lw $ra, 0($sp)
	addi $sp, $sp, 4
	jr $ra

#end of play2_input function
#play1_win is the jump of function player1_win_condition
play1_win:
	li $v0, 4
	la $a0, congrats_player1
	syscall
	j end
#play2_win is the jump of function player2_win_condition
play2_win:
	li $v0, 4
	la $a0, congrats_player2
	syscall
	j end
draw_game:
	li $v0, 4
	la $a0, tie_game
	syscall
	j end
#win_condition fuction
win_condition:
	#call another function in this function
	addi $sp, $sp, -4
	sw $ra, 0($sp)
	jal row_check
	jal column_check
	jal diagonal_check
	lw $ra, 0($sp)
	addi $sp, $sp, 4
	jr $ra
#end of win condition fucntion

#row_check_function
row_check:
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
#row 1
	lb $t0, 0($s0)
	lb $t1, 1($s0)
	lb $t2, 2($s0)
	lb $t3, 3($s0)
	lb $t4, 4($s0)
	add $t5, $t0, $t1 #the first 3 element of row 1
	add $t5, $t5, $t2
	bne $t5, 264, next_row1_x
	j play1_win
	next_row1_x:
	bne $t5, 237, next_row1_y
	j play2_win
	next_row1_y:
	add $t5, $t1, $t2 #the second 3 element of row 1
	add $t5, $t5, $t3
	bne $t5, 264, next_row1_xx
	j play1_win
	next_row1_xx:
	bne $t5, 237, next_row1_yy
	j play2_win
	next_row1_yy:
	add $t5, $t2, $t3 #the last 3 element of row 1
	add $t5, $t5, $t4
	bne $t5, 264, next_row1_xxx
	j play1_win
	next_row1_xxx:
	bne $t5, 237, next_row1_yyy
	j play2_win
	next_row1_yyy:
#row 2
	lb $t0, 0($s1)
	lb $t1, 1($s1)
	lb $t2, 2($s1)
	lb $t3, 3($s1)
	lb $t4, 4($s1)
	add $t5, $t0, $t1 #the first 3 element of row 2
	add $t5, $t5, $t2
	bne $t5, 264, next_row2_x
	j play1_win
	next_row2_x:
	bne $t5, 237, next_row2_y
	j play2_win
	next_row2_y:
	add $t5, $t1, $t2 #the second 3 element of row 2
	add $t5, $t5, $t3
	bne $t5, 264, next_row2_xx
	j play1_win
	next_row2_xx:
	bne $t5, 237, next_row2_yy
	j play2_win
	next_row2_yy:
	add $t5, $t2, $t3 #the last 3 element of row 2
	add $t5, $t5, $t4
	bne $t5, 264, next_row2_xxx
	j play1_win
	next_row2_xxx:
	bne $t5, 237, next_row2_yyy
	j play2_win
	next_row2_yyy:
#row 3
	lb $t0, 0($s2)
	lb $t1, 1($s2)
	lb $t2, 2($s2)
	lb $t3, 3($s2)
	lb $t4, 4($s2)
	add $t5, $t0, $t1 #the first 3 element of row 3
	add $t5, $t5, $t2
	bne $t5, 264, next_row3_x
	j play1_win
	next_row3_x:
	bne $t5, 237, next_row3_y
	j play2_win
	next_row3_y:
	add $t5, $t1, $t2 #the second 3 element of row 3
	add $t5, $t5, $t3
	bne $t5, 264, next_row3_xx
	j play1_win
	next_row3_xx:
	bne $t5, 237, next_row3_yy
	j play2_win
	next_row3_yy:
	add $t5, $t2, $t3 #the last 3 element of row 3
	add $t5, $t5, $t4
	bne $t5, 264, next_row3_xxx
	j play1_win
	next_row3_xxx:
	bne $t5, 237, next_row3_yyy
	j play2_win
	next_row3_yyy:
#row 4
	lb $t0, 0($s3)
	lb $t1, 1($s3)
	lb $t2, 2($s3)
	lb $t3, 3($s3)
	lb $t4, 4($s3)
	add $t5, $t0, $t1 #the first 3 element of row 4
	add $t5, $t5, $t2
	bne $t5, 264, next_row4_x
	j play1_win
	next_row4_x:
	bne $t5, 237, next_row4_y
	j play2_win
	next_row4_y:
	add $t5, $t1, $t2 #the second 3 element of row 4
	add $t5, $t5, $t3
	bne $t5, 264, next_row4_xx
	j play1_win
	next_row4_xx:
	bne $t5, 237, next_row4_yy
	j play2_win
	next_row4_yy:
	add $t5, $t2, $t3 #the last 3 element of row 4
	add $t5, $t5, $t4
	bne $t5, 264, next_row4_xxx
	j play1_win
	next_row4_xxx:
	bne $t5, 237, next_row4_yyy
	j play2_win
	next_row4_yyy:
#row 5
	lb $t0, 0($s4)
	lb $t1, 1($s4)
	lb $t2, 2($s4)
	lb $t3, 3($s4)
	lb $t4, 4($s4)
	add $t5, $t0, $t1 #the first 3 element of row 5
	add $t5, $t5, $t2
	bne $t5, 264, next_row5_x
	j play1_win
	next_row5_x:
	bne $t5, 237, next_row5_y
	j play2_win
	next_row5_y:
	add $t5, $t1, $t2 #the second 3 element of row 5
	add $t5, $t5, $t3
	bne $t5, 264, next_row5_xx
	j play1_win
	next_row5_xx:
	bne $t5, 237, next_row5_yy
	j play2_win
	next_row5_yy:
	add $t5, $t2, $t3 #the last 3 element of row 5
	add $t5, $t5, $t4
	bne $t5, 264, next_row5_xxx
	j play1_win
	next_row5_xxx:
	bne $t5, 237, next_row5_yyy
	j play2_win
	next_row5_yyy:
	jr $ra
#end of row_check function
	
#column_check function
column_check:
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
#first colum
	lb $t0, 0($s0)
	lb $t1, 0($s1)
	lb $t2, 0($s2)
	lb $t3, 0($s3)
	lb $t4, 0($s4)
	add $t5, $t0, $t1 #the first 3 element of column 1
	add $t5, $t5, $t2
	bne $t5, 264, next_column1_x
	j play1_win
	next_column1_x:
	bne $t5, 237, next_column1_y
	j play2_win
	next_column1_y:
	add $t5, $t1, $t2 #the second 3 element of column 1
	add $t5, $t5, $t3
	bne $t5, 264, next_column1_xx
	j play1_win
	next_column1_xx:
	bne $t5, 237, next_column1_yy
	j play2_win
	next_column1_yy:
	add $t5, $t2, $t3 #the last 3 element of column 1
	add $t5, $t5, $t4
	bne $t5, 264, next_column1_xxx
	j play1_win
	next_column1_xxx:
	bne $t5, 237, next_column1_yyy
	j play2_win
	next_column1_yyy:
#second column
	lb $t0, 1($s0)
	lb $t1, 1($s1)
	lb $t2, 1($s2)
	lb $t3, 1($s3)
	lb $t4, 1($s4)
	add $t5, $t0, $t1 #the first 3 element of column 2
	add $t5, $t5, $t2
	bne $t5, 264, next_column2_x
	j play1_win
	next_column2_x:
	bne $t5, 237, next_column2_y
	j play2_win
	next_column2_y:
	add $t5, $t1, $t2 #the second 3 element of column 2
	add $t5, $t5, $t3
	bne $t5, 264, next_column2_xx
	j play1_win
	next_column2_xx:
	bne $t5, 237, next_column2_yy
	j play2_win
	next_column2_yy:
	add $t5, $t2, $t3 #the last 3 element of column 2
	add $t5, $t5, $t4
	bne $t5, 264, next_column2_xxx
	j play1_win
	next_column2_xxx:
	bne $t5, 237, next_column2_yyy
	j play2_win
	next_column2_yyy:
#third column
	lb $t0, 2($s0)
	lb $t1, 2($s1)
	lb $t2, 2($s2)
	lb $t3, 2($s3)
	lb $t4, 2($s4)
	add $t5, $t0, $t1 #the first 3 element of column 3
	add $t5, $t5, $t2
	bne $t5, 264, next_column3_x
	j play1_win
	next_column3_x:
	bne $t5, 237, next_column3_y
	j play2_win
	next_column3_y:
	add $t5, $t1, $t2 #the second 3 element of column 3
	add $t5, $t5, $t3
	bne $t5, 264, next_column3_xx
	j play1_win
	next_column3_xx:
	bne $t5, 237, next_column3_yy
	j play2_win
	next_column3_yy:
	add $t5, $t2, $t3 #the last 3 element of column 3
	add $t5, $t5, $t4
	bne $t5, 264, next_column3_xxx
	j play1_win
	next_column3_xxx:
	bne $t5, 237, next_column3_yyy
	j play2_win
	next_column3_yyy:
#fourth column
	lb $t0, 3($s0)
	lb $t1, 3($s1)
	lb $t2, 3($s2)
	lb $t3, 3($s3)
	lb $t4, 3($s4)
	add $t5, $t0, $t1 #the first 3 element of column 4
	add $t5, $t5, $t2
	bne $t5, 264, next_column4_x
	j play1_win
	next_column4_x:
	bne $t5, 237, next_column4_y
	j play2_win
	next_column4_y:
	add $t5, $t1, $t2 #the second 3 element of column 4
	add $t5, $t5, $t3
	bne $t5, 264, next_column4_xx
	j play1_win
	next_column4_xx:
	bne $t5, 237, next_column4_yy
	j play2_win
	next_column4_yy:
	add $t5, $t2, $t3 #the last 3 element of column 4
	add $t5, $t5, $t4
	bne $t5, 264, next_column4_xxx
	j play1_win
	next_column4_xxx:
	bne $t5, 237, next_column4_yyy
	j play2_win
	next_column4_yyy:
#fifth column
	lb $t0, 4($s0)
	lb $t1, 4($s1)
	lb $t2, 4($s2)
	lb $t3, 4($s3)
	lb $t4, 4($s4)
	add $t5, $t0, $t1 #the first 3 element of column 5
	add $t5, $t5, $t2
	bne $t5, 264, next_column5_x
	j play1_win
	next_column5_x:
	bne $t5, 237, next_column5_y
	j play2_win
	next_column5_y:
	add $t5, $t1, $t2 #the second 3 element of column 5
	add $t5, $t5, $t3
	bne $t5, 264, next_column5_xx
	j play1_win
	next_column5_xx:
	bne $t5, 237, next_column5_yy
	j play2_win
	next_column5_yy:
	add $t5, $t2, $t3 #the last 3 element of column 5
	add $t5, $t5, $t4
	bne $t5, 264, next_column5_xxx
	j play1_win
	next_column5_xxx:
	bne $t5, 237, next_column5_yyy
	j play2_win
	next_column5_yyy:
	jr $ra
#end of column_check function	

#diagonal_check function
diagonal_check:
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
#left to right and up to down diagonal
	#main diagonal [0][0] - [4][4]
	lb $t0, 0($s0)
	lb $t1, 1($s1)
	lb $t2, 2($s2)
	lb $t3, 3($s3)
	lb $t4, 4($s4)
	add $t5, $t0, $t1 #the first 3 element of the main diagonal
	add $t5, $t5, $t2
	bne $t5, 264, LR_diagonal_1_x
	j play1_win
	LR_diagonal_1_x:
	bne $t5, 237, LR_diagonal_1_y
	j play2_win
	LR_diagonal_1_y:
	add $t5, $t1, $t2 #the second 3 element of the main diagonal
	add $t5, $t5, $t3
	bne $t5, 264, LR_diagonal_1_xx
	j play1_win
	LR_diagonal_1_xx:
	bne $t5, 237, LR_diagonal_1_yy
	j play2_win
	LR_diagonal_1_yy:
	add $t5, $t2, $t3 #the last 3 element of the main diagonal
	add $t5, $t5, $t4
	bne $t5, 264, LR_diagonal_1_xxx
	j play1_win
	LR_diagonal_1_xxx:
	bne $t5, 237, LR_diagonal_1_yyy
	j play2_win
	LR_diagonal_1_yyy:
	# the diagonal from row1 to row3
	lb $t0, 2($s0)
	lb $t1, 3($s1)
	lb $t2, 4($s2)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, LR_diagonal_2_x
	j play1_win
	LR_diagonal_2_x:
	bne $t5, 237, LR_diagonal_2_y
	j play2_win
	LR_diagonal_2_y:
	# the diagonal from row3 to row5
	lb $t0, 0($s2)
	lb $t1, 1($s3)
	lb $t2, 2($s4)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, LR_diagonal_3_x
	j play1_win
	LR_diagonal_3_x:
	bne $t5, 237, LR_diagonal_3_y
	j play2_win
	LR_diagonal_3_y:
	#the diagonal from row1 to row4
	lb $t0, 1($s0)
	lb $t1, 2($s1)
	lb $t2, 3($s2)
	lb $t3, 4($s3)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, LR_diagonal_4_x
	j play1_win
	LR_diagonal_4_x:
	bne $t5, 237, LR_diagonal_4_y
	j play2_win
	LR_diagonal_4_y:
	add $t5, $t1, $t2
	add $t5, $t5, $t3
	bne $t5, 264, LR_diagonal_4_xx
	j play1_win
	LR_diagonal_4_xx:
	bne $t5, 237, LR_diagonal_4_yy
	j play2_win
	LR_diagonal_4_yy:
	#the diagonal from row2 to row 5
	lb $t0, 0($s1)
	lb $t1, 1($s2)
	lb $t2, 2($s3)
	lb $t3, 3($s4)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, LR_diagonal_5_x
	j play1_win
	LR_diagonal_5_x:
	bne $t5, 237, LR_diagonal_5_y
	j play2_win
	LR_diagonal_5_y:
	add $t5, $t1, $t2
	add $t5, $t5, $t3
	bne $t5, 264, LR_diagonal_5_xx
	j play1_win
	LR_diagonal_5_xx:
	bne $t5, 237, LR_diagonal_5_yy
	j play2_win
	LR_diagonal_5_yy:
#right to left and up to down diagonal	
	#main diagonal [0][4] - [4][0]
	lb $t0, 4($s0)
	lb $t1, 3($s1)
	lb $t2, 2($s2)
	lb $t3, 1($s3)
	lb $t4, 0($s4)
	add $t5, $t0, $t1 #the first 3 element of the main diagonal
	add $t5, $t5, $t2
	bne $t5, 264, RL_diagonal_1_x
	j play1_win
	RL_diagonal_1_x:
	bne $t5, 237, RL_diagonal_1_y
	j play2_win
	RL_diagonal_1_y:
	add $t5, $t1, $t2 #the second 3 element of the main diagonal
	add $t5, $t5, $t3
	bne $t5, 264, RL_diagonal_1_xx
	j play1_win
	RL_diagonal_1_xx:
	bne $t5, 237, RL_diagonal_1_yy
	j play2_win
	RL_diagonal_1_yy:
	add $t5, $t2, $t3 #the last 3 element of the main diagonal
	add $t5, $t5, $t4
	bne $t5, 264, RL_diagonal_1_xxx
	j play1_win
	RL_diagonal_1_xxx:
	bne $t5, 237, RL_diagonal_1_yyy
	j play2_win
	RL_diagonal_1_yyy:
	# the diagonal from row1 to row3
	lb $t0, 2($s0)
	lb $t1, 1($s1)
	lb $t2, 0($s2)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, RL_diagonal_2_x
	j play1_win
	RL_diagonal_2_x:
	bne $t5, 237, RL_diagonal_2_y
	j play2_win
	RL_diagonal_2_y:
	# the diagonal from row3 to row5
	lb $t0, 4($s2)
	lb $t1, 3($s3)
	lb $t2, 2($s4)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, RL_diagonal_3_x
	j play1_win
	RL_diagonal_3_x:
	bne $t5, 237, RL_diagonal_3_y
	j play2_win
	RL_diagonal_3_y:
	#the diagonal from row1 to row4
	lb $t0, 3($s0)
	lb $t1, 2($s1)
	lb $t2, 1($s2)
	lb $t3, 0($s3)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, RL_diagonal_4_x
	j play1_win
	RL_diagonal_4_x:
	bne $t5, 237, RL_diagonal_4_y
	j play2_win
	RL_diagonal_4_y:
	add $t5, $t1, $t2
	add $t5, $t5, $t3
	bne $t5, 264, RL_diagonal_4_xx
	j play1_win
	RL_diagonal_4_xx:
	bne $t5, 237, RL_diagonal_4_yy
	j play2_win
	RL_diagonal_4_yy:
	#the diagonal from row2 to row 5
	lb $t0, 4($s1)
	lb $t1, 3($s2)
	lb $t2, 2($s3)
	lb $t3, 1($s4)
	add $t5, $t0, $t1
	add $t5, $t5, $t2
	bne $t5, 264, RL_diagonal_5_x
	j play1_win
	RL_diagonal_5_x:
	bne $t5, 237, RL_diagonal_5_y
	j play2_win
	RL_diagonal_5_y:
	add $t5, $t1, $t2
	add $t5, $t5, $t3
	bne $t5, 264, RL_diagonal_5_xx
	j play1_win
	RL_diagonal_5_xx:
	bne $t5, 237, RL_diagonal_5_yy
	j play2_win
	RL_diagonal_5_yy:
	jr $ra
	
#end of diagonal_check function

#already_marked_1 fucntion
already_marked_1: 
	beq $t2, 45, not_marked_1  
	li, $v0, 4
	la $a0, already_marked
	syscall
	j input_again_1
	not_marked_1:
	jr $ra
#end of already_marked_1 function

#already_marked_2 fucntion
already_marked_2: 
	beq $t2, 45, not_marked_2  
	li, $v0, 4
	la $a0, already_marked
	syscall
	j input_again_2
	not_marked_2:
	jr $ra
#end of already_marked_2 function

#check_middle_point function
check_middle_point:
	la $s2, line3
	lb $t0, 2($s2)
	beq $t0, 45, valid_data
	li, $v0, 4
	la $a0, invalid_mid
	syscall
	beq $t0, 88, storeX
	#Undo player2 move(O) due to entering middle point in the first round
	addi $t0, $zero, 45
	sb $t0, 2($s2)
	j play2_input_again_1
	storeX:
	#Undo player1 move(X) due to entering middle point in the first round
	addi $t0, $zero, 45
	sb $t0, 2($s2)
	j play1_input_again_1
	valid_data:
	jr $ra 
#end of check_middle_point fucntion
#Undo_play1 function
Undo_play1:
#call another function in this function
	addi $sp, $sp, -4
	sw $ra, 0($sp)
	li $v0, 4
	la $a0, undo_player1
	syscall
	li $v0, 5
	syscall
	add $s5, $zero, $v0
	beq $s5, 1, undo1
	j end_of_undo1
	undo1:
	li $v0, 4
	la $a0, annouce_play1
	syscall
	addi $s6, $s6, -1
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
	addi $t0, $zero, 45
	#check first line
	beq $a1,0,begin_undo_x1
	j exit_undo_x1
	begin_undo_x1:
	add $s0, $s0, $a2
	sb $t0, 0($s0)
	exit_undo_x1:
#check second line
	beq $a1,1,begin_undo_x2
	j exit_undo_x2
	begin_undo_x2:
	add $s1, $s1, $a2
	sb $t0, 0($s1)
	exit_undo_x2:
#check third line
	beq $a1,2,begin_undo_x3
	j exit_undo_x3
	begin_undo_x3:
	add $s2, $s2, $a2
	sb $t0, 0($s2)
	exit_undo_x3:
#check fourth line
	beq $a1,3,begin_undo_x4
	j exit_undo_x4
	begin_undo_x4:
	add $s3, $s3, $a2
	sb $t0, 0($s3)
	exit_undo_x4:
#check fifth line
	beq $a1,4,begin_undo_x5
	j exit_undo_x5
	begin_undo_x5:
	add $s4, $s4, $a2
	sb $t0, 0($s4)	
	exit_undo_x5:
	#print the board after undo
	jal print_tic_tac_toe
	end_of_undo1:
	lw $ra, 0($sp)
	addi $sp, $sp, 4
	jr $ra

#end of Undo_play1 function
	
#Undo_play2 function
Undo_play2:
#call another function in this function
	addi $sp, $sp, -4
	sw $ra, 0($sp)
	li $v0, 4
	la $a0, undo_player2
	syscall
	li $v0, 5
	syscall
	add $s5, $zero, $v0
	beq $s5, 1, undo2
	j end_of_undo2
	undo2:
	li $v0, 4
	la $a0, annouce_play2
	syscall
	addi $s7, $s7, -1
	la $s0, line1
	la $s1, line2
	la $s2, line3
	la $s3, line4
	la $s4, line5
	addi $t0, $zero, 45
	#check first line
	beq $a1,0,begin_undo_y1
	j exit_undo_y1
	begin_undo_y1:
	add $s0, $s0, $a2
	sb $t0, 0($s0)
	exit_undo_y1:
#check second line
	beq $a1,1,begin_undo_y2
	j exit_undo_y2
	begin_undo_y2:
	add $s1, $s1, $a2
	sb $t0, 0($s1)
	exit_undo_y2:
#check third line
	beq $a1,2,begin_undo_y3
	j exit_undo_y3
	begin_undo_y3:
	add $s2, $s2, $a2
	sb $t0, 0($s2)
	exit_undo_y3:
#check fourth line
	beq $a1,3,begin_undo_y4
	j exit_undo_y4
	begin_undo_y4:
	add $s3, $s3, $a2
	sb $t0, 0($s3)
	exit_undo_y4:
#check fifth line
	beq $a1,4,begin_undo_y5
	j exit_undo_y5
	begin_undo_y5:
	add $s4, $s4, $a2
	sb $t0, 0($s4)
	exit_undo_y5:
	#print the board after undo
	jal print_tic_tac_toe
	end_of_undo2:
	lw $ra, 0($sp)
	addi $sp, $sp, 4
	jr $ra
	
#end of Undo_play2 function
check_valid:
	slti $t0,$a1,0
	beq $t0, 1, out_of_range
	slti $t0, $a1, 5
	beq $t0, 0, out_of_range
	slti $t1,$a2,0
	beq $t1, 1, out_of_range
	slti $t1, $a2, 5
	beq $t1, 0, out_of_range
	jr $ra
out_of_range:
	li $v0, 4
	la $a0, invalid_data
	syscall
	j end

.data
line1: .space 5
line2: .space 5
line3: .space 5
line4: .space 5
line5: .space 5
instruction: .asciiz "Welcome to the tic-tac-toe game, To play this 5x5 tic-tac-toe game, you must follow these rules: \n \n"
first_rule: .asciiz "1. Any player who has 3 consecutive 'X'  or 'O' in a row, column or diagonal will be the winner. \n \n"
second_rule: .asciiz"2. In order to input the position, the player must enter the row index first and then the column index. \n   The first row has index 0 and the last row has index 4 and it is the same with column. \n   Remember that the index range is 0 to 4, if you enter the number outside of this range, the game will instantly end.\n \n"
example_input: .asciiz "For example, the top left position has the row index is 0 and the column index is 0. The middle point has the row index is 2 and the column index is 2. \n \n"
third_rule: .asciiz "3. During the first turn of both players, they are not allowed to choose the central point. (row index and column index is 2).\n \n"
fourth_rule: .asciiz "4. Players can undo one move before the opponent plays. Remember that the players have 2 times to undo. If a player uses all of their undo opportunities or wins the game, the undo function will not be displayed.\n \n"
last_rule: .asciiz "5. During the game, 'X' is for player 1 and 'O' is for player 2. \n " 
board_display: .asciiz" \n This is a 5x5 board. Enjoy the tic-tac-toe game. \n \n"
newline: .asciiz "\n"
space: .asciiz " "
player1_input_row: .asciiz " Player1, please enter the row: "
player1_input_column: .asciiz " Player1, please enter the column: "
player2_input_row: .asciiz " Player2, please enter the row: "
player2_input_column: .asciiz " Player2, please enter the column: "
invalid_mid: .asciiz " \n Cannot choose the MIDDLE position in the first round. Please enter again.\n"
already_marked: .asciiz " \n Player1 or Player2 have already MARKED this position. Please enter again. \n  "
congrats_player1: .asciiz" \n Congratulations! Player 1 won the tic-tac-toe game. \n"
congrats_player2: .asciiz" \n Congratulations! Player 2 won the tic-tac-toe game. \n"
tie_game: .asciiz" \n Draw. No one win this tic-tac-toe game.\n"
undo_player1: .asciiz " Player 1, if you want to undo, enter 1 and, else enter any number except 1. Enter number here: "
invalid_data: .asciiz " \n Player 1 or Player 2 enter an invalid index for row or column. \n"
undo_player2: .asciiz " Player 2, if you want to undo, enter 1, else enter any number except 1. Enter number here: "
annouce_play1: .asciiz" \n Player 1 has used the undo function. \n Please enter the position again.\n \n"
annouce_play2: .asciiz" \n Player 2  has used the undo function. \n Please enter the position again.\n \n"
