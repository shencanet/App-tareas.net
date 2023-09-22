<template>
    <div>
        <h1 class="siaplay-4 text-center">Listado Tareas</h1>
        <hr>
        <div class="row">
            <div class="col-lg-8 offset-lg-2">
                <div class="card mt-4">
                    <div class="card-body">
                        <div class="input-group">
                            <input type="text" v-model="tarea" class="form-control form-control-lg"
                                placeholder="Agregar Tarea">
                            <div class="input-group-append"></div>

                            <button v-on:click="agregarTarea()" class="btn btn-success btn-lg">Agregar</button>
                        </div>
                    </div>
                    <br>
                    <h4 v-if="listTarea.length == 0 ">No ahi Tareas </h4>
                    {{ listTarea}}
                   

                    <ul class="list-group">
                        <li v-for="(tarea, index) of listTarea" :key="index"
                            class="list-group-item d-flex justify-content-between">

                            <span class="cursor" v-on:click="editarTarea(tarea, index)">
                                <svg xmlns="http://www.w3.org/2000/svg" height="1em"
                                    viewBox="0 0 512 512"><!--! Font Awesome Free 6.4.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. -->
                                    <path d="M464 256A208 208 0 1 0 48 256a208 208 0 1 0 416 0zM0 256a256 256 0 1 1 512 0A256 256 0 1 1 0 256z" />
                                </svg>
                            </span>
                            {{ tarea.nombre }}
                            
                            <span class="cursor" v-on:click="eliminarTarea(index)"> 
                                <svg xmlns="http://www.w3.org/2000/svg" height="1em"
                                    viewBox="0 0 448 512"><!--! Font Awesome Free 6.4.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2023 Fonticons, Inc. -->
                                    <path
                                        d="M135.2 17.7L128 32H32C14.3 32 0 46.3 0 64S14.3 96 32 96H416c17.7 0 32-14.3 32-32s-14.3-32-32-32H320l-7.2-14.3C307.4 6.8 296.3 0 284.2 0H163.8c-12.1 0-23.2 6.8-28.6 17.7zM416 128H32L53.2 467c1.6 25.3 22.6 45 47.9 45H346.9c25.3 0 46.3-19.7 47.9-45L416 128z" />
                                </svg>
                            </span>

                        </li>
                    </ul>



                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: "Tarea_altern",
    data() {
        return {
            tarea: '',
            listTarea: [],

        }
    },
    methods: {
        agregarTarea() {
            const tarea = {
                nombre: this.tarea,
                estado: false
            }
            this.listTarea.push(tarea);
            this.tarea = '';
        },
        eliminarTarea(index) {
            this.listTarea.splice(index, 1);
        },
        editarTarea(tarea, index) {
            this.listTarea[index].estado = !tarea.estado ;
            
            
        }
    },
}
</script>

<style  scoped>
.cursor {
    cursor: pointer;
}</style>
