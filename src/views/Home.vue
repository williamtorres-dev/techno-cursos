<template>
  <div>
    <div v-if="loading">
      <PageLoading/>
    </div>
    <transition>
      <div v-if="api" class="conteudo">
        <div>
          <h1>Sobre a {{api.titulo}}</h1>
          <p>{{api.descricao}}</p>
          <router-link class="btn-cursos" tag="button" to="/cursos">Cursos</router-link>
          <div>
            <h2 class="avaliacoes">Avaliações</h2>
            <ul>
              <li v-for="avaliacao in api.avaliacoes" :key="avaliacao.nome">
                <p class="nome">{{avaliacao.nome}}</p>
                <p class="descricao">{{avaliacao.descricao}}</p>
              </li>
            </ul>
          </div>
        </div>
        <img src="@/assets/aprender.png" alt="Aprenda Web Design">
      </div>
    </transition>
  </div>
</template>

<script>
import fetchData from "@/mixins/fetchData.js";

export default {
  name: "home",
  mixins: [fetchData],
  created() {
    this.fetchData("/home");
  }
};
</script>

<style>
.btn-cursos {
  border: none;
  background: #4b8;
  border-radius: 4px;
  color: white;
  cursor: pointer;
  padding: 15px 40px;
  font-size: 1rem;
  margin-top: 10px;
  margin-bottom: 40px;
  box-shadow: 0 4px 2px rgba(0, 0, 0, 0.1);
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}

h2.avaliacoes {
  margin-bottom: 40px;
}

ul li p.nome {
  font-weight: bold;
}

ul li p.descricao {
  margin-bottom: 40px;
}

</style>
