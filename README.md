## Python
1. Run the following command
   ```
   pip install snakeviz
   ```
2. Import cProfile and so on
   ```
   import cProfile
   def your_function():
    # Your code here
   if __name__ == '__main__':
    # Profile your_function
    profiler = cProfile.Profile()
    profiler.enable()

    your_function()

    profiler.disable()
    profiler.print_stats()
   ```
3. Run the file
  ```
  python -m cProfile your_script.py
  ```
4. Run the following command with the correct path and follow the link
   ```
   snakeviz profile_data_file
   ```

## C++
1. Compile the code with the correct compiler flag `-pg`
   ```
   gcc -pg *.cpp -o app
   ```
2. Run the executable
   ```
   ./app
   ```
3. Run the profiler
   ```
   gprof app gmon.out
   ```
If necessary, you can create callgraph diagrams

4. Translate profiling data to text, create image
  ```
  gprof ./main | gprof2dot -s | dot -Tpng -o output.png
  ```

Or use google Perf tools
5. Install following this [repo](https://github.com/gperftools/gperftools)
6. Add the `libprofiler` profiler library to your library load path at runtime
7. Use pprof to generate a flat execution profile, or a callgraph diagram
  ```
  LD_PRELOAD=/usr/local/lib/libprofiler.so CPUPROFILE=main.prof CPUPROFILE_FREQUENCY=100000 ./main
  ```
8. Visualize
   ```
   pprof --text ./main main.prof
   ```


